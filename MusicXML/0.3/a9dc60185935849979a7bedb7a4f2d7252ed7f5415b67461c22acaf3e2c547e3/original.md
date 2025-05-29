```
@importMX
```

Imports all the MusicXML types in case you are sure no conflicts happens.

# Just put it in the code:

```julia
@importMX # gets translated to: import MusicXML: ScorePartwise, Part, Measure, Note, Chord, Unpitched, Rest, Pitch, Grace, Attributes, Time, Transpose, Clef, Key, PartList, ScorePart, MidiInstrument, MidiDevice, ScoreInstrument
```
