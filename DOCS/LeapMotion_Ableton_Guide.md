🖐🏻 Leap Motion  
# Ableton Live Template  
[LeapMotion-AbletonTemplate.als](TEMPLATE/LeapMotion-AbletonTemplate.als)

# 📄 Overview  
The **Leap Motion Controller**, launched in 2013 by Leap Motion Inc. (now Ultraleap), is an **infrared tracking device** capable of detecting hand and finger movements in 3D space with high precision and without physical contact. Originally designed for touchless interaction in 3D/VR environments, it was quickly adopted by artists and developers as an **alternative controller for musical instruments, effects, and interactive visuals**, thanks to its ability to transmit OSC or MIDI data in real-time.

### 📝 Review  
[Ultraleap](https://www.xrtoday.com/mixed-reality/ultraleap-leap-motion-controller-review/)

## Goal  
- Use Leap Motion as an **expressive musical controller**  
- Play **MIDI notes** in Ableton Live using spatial movements (theremin-style)  
- Map **MIDI CC or effect parameters** via hand gestures  
- Integrate Leap Motion into an **advanced hybrid setup**, maintaining flexibility and expressiveness  

### This setup enables you to:  
- Virtually play instruments through gesture (theremin-style)  
- Modulate effects in real time  
- Build a tailored template for live performance or studio work  

## ✅ Requirements  
- [Leap Motion Controller - Ultraleap](https://leap2.ultraleap.com/downloads/leap-motion-controller/)  
- Windows 10/11  
- Ableton Live 11 or 12 Suite  
- Max for Live installed  
- A virtual MIDI port using [loopMIDI](https://www.tobias-erichsen.de/software/loopmidi.html)

## 🧰 Utilities & Resources  
- [Ultraleap Gemini](https://www.ultraleap.com) | Official tracking software for Leap Motion (required on Windows 10/11)  
- [LeapmotionOSC v1.1.0](https://github.com/ThatGuyThimo/leapmotion-osc/releases) | Sends OSC messages from Leap Motion to use in Tekh Map  
- [loopMIDI](https://www.tobias-erichsen.de/software/loopmidi.html) | Creates virtual MIDI ports for internal software routing  
- [MIDI Paw](https://midipaw.com/) | Maps Leap Motion gestures to MIDI CC, pitch bend, and more  
- [Ableton Live 12](https://www.ableton.com/en/) | Main DAW to integrate instruments, effects, and controllers  
- [Tekh Map (Max for Live OSC device control)](https://thetapelessworld.com/post/93980893969/tekhmap) | Max for Live devices that convert OSC to MIDI  
- [Max for Live](https://maxforlive.com/) | Required runtime environment for Tekh Map devices  

# 📘 How To

## 🔌 Connect Leap Motion  
- Plug the Leap Motion device into your PC via USB  
- Install **Ultraleap Gemini (v5)** from [Ultraleap Gemini](https://www.ultraleap.com)

## 🟢 Launch LeapmotionOSC  
- Download [LeapmotionOSC v1.1.0](https://github.com/robbykraft/LeapmotionOSC)  
- Run the program. You should see `Controller connected` and FPS stats.  
- OSC data will be sent to **port 9000** at `127.0.0.1`

## 🎚️ Create a virtual MIDI port  
- Open **loopMIDI**  
- Click “+” and create a port named **LeapToAbleton**

## ⚙️ Configure MIDI Paw  
- Launch **[MIDI Paw](https://midipaw.com/manual/)**  
- In the top-right section:  
    - **MIDI In**: _LeapMotion_  
    - **MIDI Out**: _LeapToAbleton_  
- Create a **Performance Rule**:  
    - Choose a gesture (e.g. _Move Up/Down_)  
    - Select a MIDI message (e.g. _Modulation Wheel_, _Pitch Bend_, or _CC_)  
- In Ableton, press **Ctrl+M** to **manually map** the desired parameter

## 🎛️ Load Tekh Map Master & Note in Ableton

### Tekh Map Master  
- Drop it onto an empty MIDI track  
- Set:  
    - **OSC Input** to **9000**  
    - Click `Update DB`  
    - You’ll see hand/finger OSC inputs populate

### Tekh Map Note  
- Drop it onto a second MIDI track, or the same track as your instrument  
- Set:  
    - Output mode: `pitch`  
    - OSC input: select from the list (e.g. `/avatar/parameters/leftIndex`)  
    - MIDI note range (e.g. C2–C4)  
    - Enable `hold` and set `duration` for **sustained notes**

### 🎹 MIDI Routing in Ableton  
- Go to **Preferences > Link, Tempo & MIDI**  
    - Under **Input** for _LeapToAbleton_, check **Track** and **Remote**  
    - **Output** is optional unless you plan to send MIDI externally

![Link-Tempo-MIDI.png](https://github.com/runwithscissor/Leap-Motion-to-Ableton-Live/blob/db753c0228666fe3802f7fafd4d3ca37f49f5bdc/Link-Tempo-MIDI.png)


This setup links the virtual MIDI port created with [loopMIDI](https://www.tobias-erichsen.de/software/loopmidi.html), used in [MIDI Paw](https://midipaw.com/), with [Ableton Live 12](https://www.ableton.com/en/) and [[🖐️ Leap Motion]]

- Example routing:

| Track       | MIDI From     | Audio/MIDI To | Monitor |
|-------------|---------------|----------------|---------|
| Track 1     | Tekh Map Note | None           | In      |
| Track 2     | LeapToAbleton | Track 1        | In      |

![AL-Template-view.png](https://github.com/runwithscissor/Leap-Motion-to-Ableton-Live/blob/db753c0228666fe3802f7fafd4d3ca37f49f5bdc/AL-Template-view.png)

### 🔴 MIDI Recording  
To record MIDI notes generated by Tekh Map:  
- Create a **MIDI merger track**  
- `MIDI From`: Tekh Map Note + MIDI Paw  
- `MIDI To`: your instrument track  
- Record on the merger track, or route it to another armed track

## 🧪 Troubleshooting

| Issue                             | Solution                                                                 |
|----------------------------------|--------------------------------------------------------------------------|
| Tekh Map Note receives no data   | Make sure LeapmotionOSC is running and port 9000 is set correctly        |
| MIDI Paw doesn’t affect anything | Use **Ctrl+M** in Live and move your hand to assign control              |
| Leap Motion not recognized       | Check that Gemini is running (green icon), and restart if needed         |
| No MIDI notes recorded           | Confirm routing and set Monitor to **In** on the correct track           |

## 📎 Conclusion  
With this setup, Leap Motion becomes a **performative and expressive controller** for Ableton Live. The interplay between **spatial gestures**, **sound**, and **modulation** unlocks truly unique, fluid, and personal audiovisual performances.

### 📦 Optional next steps:  
- Build a reusable **Ableton Live template**  
- Add **Tekh Map Dial** to control other MIDI parameters  
- Record performances and sync with TouchDesigner for **interactive visuals**
