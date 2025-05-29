```
Materials(
    name::AbstractString,
    els::AbstractArray{Element},
    ::Type{U},
    dims::Tuple;
    atomicweights::AbstractDict{Element,V} = Dict{Element,Float64}(),
    properties::AbstractDict{Symbol,Any} = Dict{Symbol,Any}(),
) where {U<:AbstractFloat, V<:AbstractFloat}
```

A type to represent the composition of multiple points as a complement to `KRatios` and `HyperSpectrum`. The data is stored in a much more memory efficient manner than `Array{Material}` would but can be accessed either by coordinate like `mats[1,2]` returning a `Material` or by element like `mats[n"Fe"]` returning an Array of mass fraction values.
