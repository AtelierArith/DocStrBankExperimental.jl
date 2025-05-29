```
drawLSystem(lsystem::LSystem ;
       # optional settings:
       forward=15,
       turn=45,
       iterations=10,
       filename="lsystem.png",
       width=800,
       height=800,
       startingpen=(0.3, 0.6, 0.8), # starting color RGB
       startingx=0,
       startingy=0,
       startingorientation=0,
       showpreview=true,
       backgroundcolor = colorant"black",
       asteriskfunction = (t::Luxor.Turtle) -> ())
```

Draw a Lindenmayer system. `lsystem` is the definition of a L-System (rules followed by initial state).

For example:

```
newsystem = LSystem(Dict("F" => "AGCFCGAT", "G" => "CFAGAFC"), "F")
```

You can change or add rules like this:

```
newsystem.rules["F"] = "OFO"
```

You can vary the line width using Turtle commands "1" ... "9" to select the appropriate line width (in points), or "n" to choose a narrow 0.5.
