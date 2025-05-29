```
struct ExplicitModalLogiset{
    W<:AbstractWorld,
    U,
    FT<:AbstractFeature,
    FR<:AbstractFrame{W},
} <: AbstractModalLogiset{W,U,FT,FR}

    d :: Vector{Tuple{Dict{W,Dict{FT,U}},FR}}

end
```

A logiset where the features are boolean, and where each instance associates to each world the set of features with `true`.

See also [`AbstractModalLogiset`](@ref).
