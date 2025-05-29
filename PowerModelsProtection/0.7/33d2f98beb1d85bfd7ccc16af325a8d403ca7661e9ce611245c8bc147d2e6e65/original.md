```
add_relay(data::Dict{String,Any}, element1::String, element2::String, id::String, trip_angle::Number;
kwargs...)
```

Function that adds a directional differential relay to circuit. In order to use properly circuit file must be edited so that the line we are concerned with is divided in two with a bus in between. Fault can then be added to that bus. Will use phase angles of current and voltage at either side to determine if direction of power is same on both ends. Element1 is from, element2 is to. Inputs:     Required         (1) data(Dictionary): A dictionary that comes from parse*file() function of .dss file.         (2) element1(String): First circuit element relay is protecting.         (3) element2(String): Second circuit element relay is protecting. For relay to work properly elements should each be a protection                                 of the same line with bus in between them where the fault will be simulated.         (4) id(String): Relay id.         (5) trip*angle: Angle at which relay will trip if the difference in phase angles is greater.

```
Optional
    (6) kwargs: Any additional that user wants. Not used for anything else.
```

Outputs:     Adds a differential relay to the data dictionary. Basically adds an element to the circuit that is defined in     the .dss file.
