```
add_relay(data::Dict{String,Any}, element::String, id::String, TS::Number, TDS::Number;
phase::Vector=[1,2,3],t_breaker::Number=0, shots::Int=1, kwargs...)
```

Function that adds an overcurrent relay with no CT to desired element on each desired phase. To call: add*relay(ciruit*dictionary, "circuit*element", "name", TS(Amps),TDS;         kwargs(format:t*c=1.0))

Inputs:     Required(5)         (1) data(Dictionary): A dictionary that comes from parse*file() function of .dss file.         (2) element(String): Circuit element that relay is protecting/connected to.         (3) id(String): Relay id for multiple relays on same zone (primary, secondary, etc)         (4) TS(Float): Tap setting of relay. (do not include CT)         (5) TDS(Float): Time dial setting     Optional         (6) phase(Vector): Optional. Phases that relay is connected/protecting. Defaults to 3 phase:[1,2,3](7) t*breaker(Number): Optional. Operation time of the breaker.         (8) Shots(Int): Optional. Number of operations before lockout.         (9) kwargs: Any additional that user wants. Not used for anything else.

Outputs:     Adds a relay to the data dictionary. Basically adds an element to the circuit that is defined in     the .dss file.
