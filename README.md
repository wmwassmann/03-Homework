# 03-Homework
03-Homework


// I had fun with this one.  Though I feel like I could have done more to stylize it to my liking.  Still learning! I have loads of ideas for homework 4

    alert("Welcome to the 'Alert Driven' Custom Deluxe Ulta-Durable Password Generator 5000! (tm)");
    alert("To confirm a section, press'Okay.' To decline a selection, press 'Cancel.'");
    alert("In order to fully appreciate the power of the 'Alert Driven' Custom Deluxe Ultra-Durable Password Generator 5000 (tm), we recommend you choose all available fields.")

// I feel like there's a more efficient way to do this. I did some googling and I found there's a way to do it with what appeared to be a character index? Where you just refer to a number in a preset list - but I wanted to keep it in the spirit of the homework and did the arrays. I think I might try it the other way in my spare time.

    lowerCase = ["a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"]
    upperCase = ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"]
    numbers = ["0","1","2","3","4","5","6","7","8","9"]
    specialChar = ["`","~","!","@","#","$","%","^","&","*","(",")","-","_","-","+","=",",","<",".",">",";",":","'","[","]","{","}"]

// Setting up our clicker for the button.

    var get = document.querySelector("#gen");
    get.addEventListener("click", function () {
        myPassword = genPass();
        document.getElementById("final-pass").placeholder = myPassword;
    });

/ A quicky function to ensure that the user stays within the parameters.

    function genPass() {
       generate = parseInt(prompt("Enter a value between 8 and 128 to designate the length of your custom Password."));
    if (generate < 8 || generate > 128) {
        generate = parseInt(prompt("Please select a number between 8 and 128"));
    } else {
        confirmLower = confirm("Include lowercase letters?");
        confirmUpper = confirm("Include uppercase letters?");
        confirmNumber = confirm("Include numbers?");
        confirmSpecial = confirm("Include special characters?");        
    };
    
    // This was a nightmare to get right. I really hope it works all the way through.  I am pretty sure I've tested all of the different combinations - so fingers crossed I didn't miss any.  
    // Also I wasn't sure how to make something "not true" without just writing a billion lines of code, so I googled it and found the "!". Also concat was a neat little find.
       
    if (!confirmLower && !confirmUpper && !confirmNumber && !confirmSpecial) {
       alert("Please select something. 'Nothing' is a dreadful password after all.");
    } else if (confirmLower && confirmUpper && confirmNumber && confirmSpecial) {
        selections = lowerCase.concat(upperCase, numbers, specialChar);
    } else if (confirmLower && confirmUpper && confirmNumber) {
        selections = lowerCase.concat(upperCase, numbers);
    } else if (confirmLower && confirmUpper && confirmSpecial) {
        selections = lowerCase.concat(upperCase, special);
    } else if (confirmLower && confirmNumber && confirmSpecial) {
        selections = lowerCase.concat(numbers, special);
    } else if (confirmUpper && confirmNumber && confirmSpecial) {
        selections = upperCase.concat(numbers, special);
    } else if (confirmUpper && confirmNumber && confirmSpecial) {
        selections = upperCase.concat(numbers, special);
    } else if (confirmLower && confirmUpper) {
        selections = lowerCase.concat(upperCase);
    } else if (confirmLower && confirmNumber) {
        selections = lowerCase.concat(numbers);
    } else if (confirmLower && confirmSpecial) {
        selections = lowerCase.concat(special);
    } else if (confirmUpper && confirmNumber) {
        selections = upperCase.concat(numbers);
    } else if (confirmUpper && confirmSpecial) {
        selections = upperCase.concat(special);
    } else if (confirmNumber && confirmSpecial) {
        selections = numbers.concat(special);
    } else if (confirmLower) {
        selections = lowerCase;
    } else if (confirmUpper) {
        selections = upperCase;
    } else if (confirmNumber) {
        selections = numbers;
    } else if (confirmSpecial) {
        selections = special; 
    };
  
  // Pulling random (whole) numbers from our arrays using Math.floor to ensure we get a whole number. 
  // I used .push to chuck a different new variable on the end of the generated string dependant on whatever the user chooses. 
  
    var finalPass = [];
    for (var i = 0; i < generate; i++) {
        var select = selections[Math.floor(Math.random() * selections.length)];
        finalPass.push(select);
    }
    
   // .Join ensures that they are all strung together in the return.
    var myPassword = finalPass.join("");
    UserInput(myPassword);
    return(myPassword);      
    }    
   
   // I wanted to the display the text in the "finalPass" id rather than up in the alert.
    function UserInput(myPassword) {
        document.getElementById("finalPass").textContent = myPassword;
    }

    // Still working on this part.  It's not selecting and I'm not entirely sure why. It's been a nice little headache :D
    
    const finalPass = document.getElementById("finalPass"); 
    const clip = document.getElementById("clip"); 

    clip.onClick = function () {
        clip.select();
    };

    // I've tried a few different methods and as it's extra credit, I think I'll keep working at it and see what happens.  As of right now, it's not coming to me for some reason.

