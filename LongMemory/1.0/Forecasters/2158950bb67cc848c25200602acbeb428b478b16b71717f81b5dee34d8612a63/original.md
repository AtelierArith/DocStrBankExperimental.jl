```
hitransform(x::Array)
```

Computes the harmonic inverse transformation of a time series. For more details see Hassler and Hosseinkouchack (2020).

# Arguments

  * `x::Array`: The time series.

# Output

  * `x::Array`: The time series after the harmonic inverse transformation.

# Notes

The harmonic inverse transformation is computed using the FFT.

# Examples

```julia
julia> hitransform(fi_gen(100,0.2))
```
