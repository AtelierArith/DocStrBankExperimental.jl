```julia
get_radial_roots(
    metric::Krang.Kerr{T},
    η,
    λ
) -> NTuple{4, Any}

```

Returns roots of $r^4 + (a^2-η-λ^2)r^2 + 2(η+(a-λ)^2)r - a^2η$

# Arguments

  * `metric`: Kerr{T} metric
  * `η`  : Reduced Carter constant
  * `λ`  : Reduced azimuthal angular momentum
