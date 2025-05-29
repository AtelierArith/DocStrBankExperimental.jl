```
Inputs(
    dssfilepath::String, 
    substation_bus::String;
    Pload::AbstractDict=Dict(), 
    Qload::AbstractDict=Dict(), 
    Sbase=1, 
    Vbase=1, 
    v0, 
    v_lolim=0.95, 
    v_uplim=1.05,
    Ntimesteps=1, 
    P_up_bound=1e4,
    Q_up_bound=1e4,
    P_lo_bound=-1e4,
    Q_lo_bound=-1e4,
    relaxed=true,
    extract_phase::Int=0  # set to 1, 2, or 3
)
```

Inputs constructor that parses a openDSS file for the network. If `Pload` and `Qload` are not provided then the loads are also parsed from the openDSS file.

If `extract_phase` is set to 1, 2, 3 then the loads for that phase are put into `Pload` and `Qload` and the impedance values are set to the positive sequence impedance for each line. Note that single phase lines and two phase lines do not have positive sequence definitions but single phase lines only have one impedance value anyway and for two phase lines we use  z*mutual = z12 and z*self = 1/2(z11 + z22).
