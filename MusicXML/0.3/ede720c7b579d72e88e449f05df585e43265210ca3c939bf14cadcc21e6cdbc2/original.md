```
pitch2xml(pitch)
```

Return the musicxmls values of the given pitch (MIDI)

pitch::UInt8 : starting from C-1 = 0, adding one per semitone.

![Step Alter Octave on Staff](docs/pitchesonstaff.png) ![Pitch on Guitar](docs/pitchesonguitar.png) ![Pitch on Full Keyboard](docs/fullpiano.gif)

Modified from MIDI.jl

# Examples:

```julia
pitch = 0 # for C-1
step, alter, octave = pitch2xml()
```
