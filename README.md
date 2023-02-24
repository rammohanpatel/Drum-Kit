# Drum-Kit

//HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="drumkit.css">
    <title>Drum-Kit</title>
</head>
<body>
       <div>
              
       <h1 id="heading">Drum-Kit</h1>
       </div>
    <div class="keys">
        <div data-key="65"  class="key">
              <kbd>A</kbd>
              <span class="sound">Clap</span>
                                             
        </div>
        <div data-key="83" class="key">
               <kbd>S</kbd>
               <span class="sound">Hihat</span>
        </div>
        <div data-key="68" class="key">
               <kbd>D</kbd>
               <span class="sound">Kick</span>
        </div>
        <div data-key="70" class="key">
               <kbd>F</kbd>
               <span class="sound">Openhat</span>
        </div>
        <div data-key="71" class="key">
               <kbd>G</kbd>
               <span class="sound">Boom</span>
        </div>
        <div data-key="72" class="key">
               <kbd>H</kbd>
               <span class="sound">Ride</span>
        </div>
        <div data-key="74" class="key">
               <kbd>J</kbd>
               <span class="sound">Snare</span>
        </div>
        <div data-key="75" class="key">
               <kbd>K</kbd>
               <span class="sound">Tom</span>
        </div>
        <div data-key="76" class="key">
               <kbd>L</kbd>
               <span class="sound">Tink</span>
        </div>
    </div>

    <audio data-key="65" src="audio/clap.mp3"></audio>
    <audio data-key="83" src="audio/hihat.mp3"></audio>
    <audio data-key="68" src="audio/kick.mp3"></audio>
    <audio data-key="70" src="audio/ohat.mp3"></audio>
    <audio data-key="71" src="audio/boom.mp3"></audio>
    <audio data-key="72" src="audio/ride.mp3"></audio>
    <audio data-key="74" src="audio/snare.mp3"></audio>
    <audio data-key="75" src="audio/tom.mp3"></audio>
    <audio data-key="76" src="audio/tink.mp3"></audio>

<script>
        window.addEventListener("keydown",function(e)
        {
        const audio=document.querySelector(`audio[data-key="${e.keyCode}"]`);
        var key=document.querySelector(`.key[data-key="${e.keyCode}"]`);
        
       if(!audio) return;
       audio.currentTime=0;
       audio.play();
       key.classList.add('playing');
       });
function removetransition(e)
    {
        if(e.propertyName!=='transform') return; 
        this.classList.remove('playing') ;  
    }
const keys=document.querySelectorAll('.key');
keys.forEach(key => key.addEventListener('transitionend',removetransition));

 </script>

    
</body>
</html>

//CSS

*{
    margin: 0;
    padding: 0;
}
body{
    background-image: url(drumkit_img/drumkit.jpg);
}
.keys{
    top:20vh ;
    height: 20vh;
    display: flex;
    position: relative;
    margin: 0 auto;
    border: 2px solid #dfdeeae4;
    justify-content: space-evenly;
    align-items: center;
}
.key{
    margin: 2px 5px;
    border-radius: 3px;
    border: 2px solid rgb(158, 224, 27);
    height: 50%;
    width:8%;
    text-align:center;
    background-color: rgba(0,0,0,0.4);
    transition: all 0.07s  ;
}
kbd{
    display: block;
    font-size: 30px;
    color: bisque;
}
span{
    
    font-size: 20px;
    color: rgb(11, 255, 255);
    text-transform: uppercase;
    text-align: center;
    letter-spacing: 2px;
}
.playing
{
    transform: scale(1.5);
    border-color: #ffc600;
    box-shadow:0 0 1rem #ffc600 ;
}
#heading{
    display: flex;
    font-size: 100px;
    text-align: center;
    justify-content: space-between;
    color:gold;
    width: 500px;
    margin-left:auto;
    margin-right: auto;
    z-index: 20;
    margin-top: 10px;
    
   
}
