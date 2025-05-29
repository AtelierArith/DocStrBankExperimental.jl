```julia
total_mino_time(
    metric::Krang.Kerr{T},
    roots::NTuple{4, T} where T
) -> Any

```

Returns the maximum mino time that can be accrued along a ray.

# Arguments

  * `metric` : Kerr metric
  * `roots` : Roots of the radial potential
  * `I0_inf` : Mino time at infinity
