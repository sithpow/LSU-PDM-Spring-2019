# Project Setup

## Editor
- [Visual Studio Code](https://code.visualstudio.com/), my choice
- Others
  - Atom
  - Sublime
---
## Local Server
- [Download Node](https://nodejs.org/en/)
- Choose from these servers
  * [lite-server](https://www.npmjs.com/package/lite-server)
  * [http-server](https://www.npmjs.com/package/http-server)
  * [browser-sync](https://www.browsersync.io/)
    * host folders with ```browser-sync start -s --directory -f ./ ```

---

# Assignment 1: Build a sampler 

- [assignment](https://moodle3.lsu.edu/mod/assign/view.php?id=988727)
- [project starter](https://github.com/tatecarson/LSU-PDM-Spring-2019/tree/master/Week_1_T/0_p5-tone-starter)
  

---

# WEBAUDIO BASICS & SOUND FILE PLAYERS

---

## Understanding the Audio Signal Path

![null](https://d33wubrfki0l68.cloudfront.net/456ff8140850b3122895b86c7d9f2743e4f3d480/593ce/images/uploads/simple_audio_pathway-1-.png)

ex:

```javascript
var player = new Tone.Player().toMaster();
```

---

## Creating a Sound File Player

<iframe height="300" style="width: 100%;" scrolling="no" title="PDM Sound: Sample Playback" src="//codepen.io/lsuddem/embed/MXVgVR/?height=300&theme-id=35490&default-tab=result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/lsuddem/pen/MXVgVR/'>PDM Sound: Sample Playback</a> by LSU DDEM
  (<a href='https://codepen.io/lsuddem'>@lsuddem</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

[starter template](https://codepen.io/lsuddem/pen/qgYmGr)
---

## Playing Multiple Sounds with Tone.Players

note: 
Instead of making multiple single-file soundfile players, we can build one Tone.Players instrument and load it with multiple soundfiles. To define which sounds to play we create an object with multiple file paths (done by opening a pair of { } brackets inside of the Tone.Players functions parenthesis), each with a unique name to call the sound up by later. You can think of this name as a type of variable that is inside of an object. 


Since we are now dealing with multiple sound files, we should cover some of the best ways to trigger individual sounds in your project, as well as ways to modulate and manipulate those sounds while they are playing.

---

### Triggering and changing sounds

- keyIsDown
- <button> Buttons</button> 
- sliders.   <input type="range" min="1" max="100" value="50" class="slider" id="myRange">


note:
Since we have multiple sounds to play now we can use keys on the keyboard to trigger them. To do that we use the p5 function keyIsDown. The embedded code below shows this method in action.

---

#### Starting the sounds

To get each specific sound to play we use a special syntax: players.get("samplename"). In this case we do either players.get("bells") to select the bells sound or players.get("arpeggio”) to play the arpeggiated synthesizer sound. Then we call .start() on the same line to play those sounds.

---

{{% codepen 500 vrzEjR %}}

#### Using buttons

Instead of using **keyIsDown** we can create buttons to trigger sounds. The below example is the same as the previous one just now we use buttons.

We create a button with the p5 function **createButton**. Inside the ('') we give the button text to display.

```
createButton("button label");
```

We can then customize the button by modifying some of its properties.
**button1.position(x, y)** determines the button location.

**button1.mousePressed()** calls a function that we define below. Inside of this function put any code that you want to run when you click the button. In the embedded example below, we made three new functions: play1, play2, and play3. Inside of each, we have our **multiplayer.get("samplename").start()** function that causes the Tone.Players object to grab and play the corresponding sound file:

{{% codepen 500 OEoZyQ %}}

#### Using sliders

To change an aspect of our sound while it is playing we can use a slider. To make a slider in p5.js use createSlider().

##### Syntax

```
createSlider(min,max,[value],[step]);
```

##### Parameters

* _min_ - minimum value of the slider
* _max_ - maximum value of the slider
* _value_ - default value of the slider
* _step_ - step size for each tick of the slider (if step is set to 0, the slider will move continuously from the minimum to the maximum value)

{{% notice tip %}}
Remember: when a function's arguments are listed inside of flat brackets ina syntax example or on an API document, this indicates that those arguments are optional, and are not required in order for the function to run successfully. In the case of createSlider(), the first two arguments (min and max) are required, while the second two (value and step) can be added if you'd like to have more control over how your slider behaves.
{{% /notice %}}

To get the current value of the slider and use it in your code, call for slider.value() and attach it to a property of your player. 

#### Labeling your sampler

It's a good idea to label any sliders used to control your sampler so that you know what they do. Here is a quick reminder of how the text() function works: 

##### Syntax

```
text(str,x,y);
```

##### Parameters

*  _str_ - the alphanumeric symbols to be displayed- x-coordinate of text
*  _y_ - the y axis coordinate of text
*  _x_ - the x axis coordinate of text

In the code below, we use a button to trigger the playback of each sound and  a slider, labeled "\[File Name] Playback Speed" to change the playback speed rate of our sound while it plays:

{{% codepen 500 LrJrVe %}}