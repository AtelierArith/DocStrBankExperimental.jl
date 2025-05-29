```
get_var(
    filename       ::String,
    params         ::Dict{String,String},
    varnr          ::Integer,
    precision      ::DataType=Float32;
    slicex         ::AbstractVector{<:Integer}=Int[],
    slicey         ::AbstractVector{<:Integer}=Int[],
    slicez         ::AbstractVector{<:Integer}=Int[]
    )
```

Load variable nr. `varnr` from `filename`. The variable could be either primary or auxiliary. Slicing the snapshot is optional. Assumes single precision snapshot by default.
