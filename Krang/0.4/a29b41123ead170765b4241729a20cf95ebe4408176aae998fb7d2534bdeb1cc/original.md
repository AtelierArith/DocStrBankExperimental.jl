```julia
penrose_walker(
    metric::Krang.Kerr{T},
    r,
    θ,
    p_u::AbstractVector,
    f_u::AbstractVector
) -> Tuple{Any, Any}

```

Returns the Penrose walker constant for a photon with momentum p*u emitted from a fluid particle with momentum f*u.
