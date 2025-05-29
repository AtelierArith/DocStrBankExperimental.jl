```
struct ExplicitBooleanModalLogiset{
    W<:AbstractWorld,
    FT<:AbstractFeature,
    FR<:AbstractFrame{W},
} <: AbstractModalLogiset{W,Bool,FT,FR}

    d :: Vector{Tuple{Dict{W,Vector{FT}},FR}}

end
```

A logiset where the features are boolean, and where each instance associates to each world the set of features with `true`.

See also [`AbstractModalLogiset`](@ref).
