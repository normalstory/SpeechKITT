# Speech KITT
<img src="https://raw.githubusercontent.com/TalAter/SpeechKITT/master/demo/README-logo.png" align="right" />

> A flexible GUI for interacting with Speech Recognition

Speech KITT makes it easy to add a GUI to sites using Speech Recognition. Whether you are using [annyang](https://github.com/TalAter/annyang), a different library or webkitSpeechRecognition directly, KITT will take care of the GUI.

Speech KITT provides a graphical interface for the user to start or stop Speech Recognition and see its current status. It can also help guide the user on how to interact with your site using their voice, providing instructions and sample commands. It can even be used to carry a natural conversation with the user, asking questions the user can answer with his voice, and then asking follow up questions.

Speech KITT is fully customizable, and comes with many different themes (and instructions on how to create your own designs).

[![Speech Recognition GUI with Speech KITT](https://raw.githubusercontent.com/TalAter/SpeechKITT/master/demo/speechkitt-demo.gif)](https://github.com/TalAter/SpeechKITT)


## Hello World

The most basic implementation requires 6 commands.

1. Let KITT know how to start and stop the SpeechRecognition engine you use with `SpeechKITT.setStartCommand()` and `SpeechKITT.setAbortCommand`.
2. Add events to your SpeechRecognition engine so it calls `SpeechKITT.onStart()` when it starts, and `SpeechKITT.onEnd()` when it stops.
3. Tell KITT which stylesheet to use for its GUI with `SpeechKITT.setStylesheet()` (KITT comes with a number of pre-made [styles](https://github.com/TalAter/SpeechKITT/tree/master/dist/themes)).
4. Start your engines with `SpeechKITT.vroom()`

````html
<script src="//cdnjs.cloudflare.com/ajax/libs/SpeechKITT/1.0.0/speechkitt.min.js"></script>
<script>
// Init the browser's own Speech Recognition
var recognition = new webkitSpeechRecognition();

// Tell KITT the command to use to start listening
SpeechKITT.setStartCommand(function() {recognition.start()});

// Tell KITT the command to use to abort listening
SpeechKITT.setAbortCommand(function() {recognition.abort()});

// Register KITT's recognition start event with the browser's Speech Recognition
recognition.addEventListener('start', SpeechKITT.onStart);

// Register KITT's recognition end event with the browser's Speech Recognition
recognition.addEventListener('end', SpeechKITT.onEnd);

// Define a stylesheet for KITT to use
SpeechKITT.setStylesheet('//cdnjs.cloudflare.com/ajax/libs/SpeechKITT/1.0.0/themes/flat.css');

// Render KITT's interface
SpeechKITT.vroom(); // SpeechKITT.render() does the same thing, but isn't as much fun!
</script>
````

## Hello World - With annyang

If you're doing [Speech Recognition with annyang](https://www.talater.com/annyang/), you can skip most of the configuration above. Just calling `SpeechKITT.annyang()` will take care of the configuration explained in steps 1 & 2 above.

````html
<script src="//cdnjs.cloudflare.com/ajax/libs/annyang/2.4.0/annyang.min.js"></script>
<script src="//cdnjs.cloudflare.com/ajax/libs/SpeechKITT/1.0.0/speechkitt.min.js"></script>
<script>
if (annyang) {
  // Add our commands to annyang
  annyang.addCommands({
    'hello': function() { alert('Hello world!'); }
  });

  // Tell KITT to use annyang
  SpeechKITT.annyang();

  // Define a stylesheet for KITT to use
  SpeechKITT.setStylesheet('//cdnjs.cloudflare.com/ajax/libs/SpeechKITT/1.0.0/themes/flat.css');

  // Render KITT's interface
  SpeechKITT.vroom();
}
</script>
````

## API Docs

For details on all available methods, options and more details, check out the [API documentation](https://github.com/TalAter/SpeechKITT/blob/master/docs/README.md).

## Pretty Badges

[![Build Status](https://travis-ci.org/TalAter/SpeechKITT.svg?branch=master)](https://travis-ci.org/TalAter/SpeechKITT)

### Author

Tal Ater: [@TalAter](https://twitter.com/TalAter)

### License

Licensed under [MIT](https://github.com/TalAter/SpeechKITT/blob/master/LICENSE).
