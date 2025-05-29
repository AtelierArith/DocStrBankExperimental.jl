```
@MX
```

A macro that adds `MX.` to the name of the MusicXML types.

Since MusicXML's types are not exported from the package to avoid conflicts with the similarly named types from other libraries (such as `Dates.Time`, `MIDI.Note`), `@MX` is given that facilitates using MusicXML types.

`@MX` assumes that all the types with these kinds of names inside in front of a macro, between `()`, or between `begin end` are MusicXML types unless explicitly written (e.g. `MIDI.Note`).

!!! warn
    It will replace the name of the types if they are used inside strings.


# Examples

```julia
@MX begin
    Note(pitch = Pitch(step = "C", alter = 0, octave = 4), duration =  4))
    # all the code ...
end
```

is translated to:

```julia
    MX.Note(pitch = Pitch(step = "C", alter = 0, octave = 4), duration =  4))
```

Type is untouched if it is called explicitly from another library:

```julia
@MX Dates.Time(12,53,40)
```

remains as:

```julia
Dates.Time(12,53,40)
```
