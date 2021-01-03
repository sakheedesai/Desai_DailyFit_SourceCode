//global variable p1Score is defined so the score can be maintained across screens and the main function is called 
var p1Score = 0;
main();

//main function  that calls the other three. also includes the on events needed to navigate app 
function main(){
  startGame();
  onEvent("button1", "click", function() {
    setScreen ("water")});
  onEvent("button2", "click", function() {
   setScreen("step");});
  onEvent("button3", "click", function() {
    setScreen("hours");});
  onEvent("button4", "click", function() {
    setScreen("calories");});
  goHome();
  //this onevent calls the funtction gameOver which determines whether the user is done or not 
  onEvent("check", "click", function(){
    checkGameover();
  });
}

//Contains onEvents for each subcategory with if statements checking a condition to increase total score and switch screen
function startGame(){
  onEvent("go", "click", function() {
   setScreen("selection_screen");
   p1Score = 0;
   hideElement("text_area");
});

onEvent("submit", "click", function() {
  setScreen("selection_screen");
  if (getText("answer") >= 8) {
    p1Score = p1Score + 1;}
    setText("score1_label", p1Score);
     hideElement("text_area");
});

  onEvent("steps_sub", "click", function() {
  setScreen("selection_screen");
  if (getText("steps_answ") >= 10000) {
    p1Score = p1Score + 1;}
    setText("score1_label", p1Score);
       hideElement("text_area");
});

  onEvent("hours_sub", "click", function() {
    setScreen("selection_screen");
    if (getText("hours_answ") >= 1) {
      p1Score = p1Score + 1;}
      setText("score1_label", p1Score);
         hideElement("text_area");
});

   onEvent("calories_sub", "click", function() {
    setScreen("selection_screen");
    if (getText("calories_answ") <= 2500) {
      p1Score = p1Score + 1;}
      setText("score1_label", p1Score);
         hideElement("text_area");
});
}

//contains the onevents associated with each return button 
function goHome(){
  onEvent("goback1", "click", function() {
  setScreen("selection_screen");
  });
  onEvent("goback2", "click", function() {
  setScreen("selection_screen");
  });
  onEvent("goback3", "click", function() {
  setScreen("selection_screen");
  });
  onEvent("goback4", "click", function() {
  setScreen("selection_screen");
  });
  onEvent("return", "click", function() {
  setScreen("welcome");
  });
  onEvent("playAgain", "click", function() {
  setScreen ("welcome");
  });
  }

// manages complexity by checking score if a button is clicked and switching screen if 4 or else displaying error message
function checkGameover() {
if (p1Score==4) {
  setScreen("gameOver");
} else {
  showElement("text_area");
}
}
