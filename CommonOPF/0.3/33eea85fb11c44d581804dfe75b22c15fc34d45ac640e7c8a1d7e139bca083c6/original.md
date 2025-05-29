```
singlephase38linesInputs(;
    Pload=Dict{String, AbstractArray{Real, 1}}(), 
    Qload=Dict{String, AbstractArray{Real, 1}}(), 
    T=24,
    loadnodes = ["3", "5", "36", "9", "10", "11", "12", "13", "15", "17", "18", "19", "22", "25", 
                "27", "28", "30", "31", "32", "33", "34", "35"],
    Sbase = 1e6,
    Vbase = 12.5e3,
    v0=1.0,
    v_uplim = 1.05,
    v_lolim = 0.95,
)
```

Convenience function for creating a single phase network with 38 lines and nodes.  Taken from: Andrianesis et al. 2019 "Locational Marginal Value of Distributed Energy Resources as Non-Wires Alternatives"

NOTE that Inputs is a mutable struct (s.t. loads can be added later).
