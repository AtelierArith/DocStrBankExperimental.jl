```
add_relay(data::Dict{String,Any}, element::String, id::String, TS::Number, TDS::Number, CTs::Vector{String};
phase::Vector=[1,2,3], t_breaker::Number=0, kwargs...)
```

Function that adds a differential relay to a bus or line. Assumes that the secondary turns of the CTs is the rated current for the corresponding branch in the relay. Uses tap setting and the total rated currents to calculate the slope of the restraint curve. "restraint" key is the slope. Note: relays on the lines will never trip because no faults can be on a line. Inputs:     Required         (1) data(Dictionary): A dictionary that comes from parse*file() function of .dss file.         (2) element(String): Circuit element that relay is protecting/connected to.         (3) id(String): Relay id for multiple relays on same zone (primary, secondary, etc)         (4) TS(Float): Tap setting of relay. Is the minimum difference current for trip.         (5) TDS(Float): Time dial setting         (6) CT1(Vector): Vector of CTs that are used. For lines there should only be one, but for busses you need one for each line                             in and out of the bus. Function will make sure you have enough.     Optional         (7) phase(Vector): Optional. Phases that relay is connected/protecting. Defaults to 3 phase:[1,2,3](8) t*breaker(Number): Optional. Operation time of the breaker.         (9) kwargs: Any additional that user wants. Not used for anything else.

Outputs:     Adds a differential relay to the data dictionary. Basically adds an element to the circuit that is defined in     the .dss file.
