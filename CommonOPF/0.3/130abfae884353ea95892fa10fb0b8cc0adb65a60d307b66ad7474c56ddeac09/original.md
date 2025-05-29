```
Inputs(
    edges::Array{Tuple}, 
    linecodes::Array{String}, 
    linelengths::Array{Float64}, 
    phases::Vector{Vector},
    substation_bus::String;
    Pload, 
    Qload, 
    Sbase=1, 
    Vbase=1, 
    Zdict, 
    v0, 
    v_lolim=0.95, 
    v_uplim=1.05,
    Ntimesteps=1, 
    P_up_bound=1e4,
    Q_up_bound=1e4,
    P_lo_bound=-1e4,
    Q_lo_bound=-1e4,
    Isquared_up_bounds=Dict{String, Float64}(),
    relaxed=true
)
```

Lowest level Inputs constructor (the only one that returns the Inputs struct). 

!!! note
    The real and reactive loads provided are normalized using `Sbase`.

