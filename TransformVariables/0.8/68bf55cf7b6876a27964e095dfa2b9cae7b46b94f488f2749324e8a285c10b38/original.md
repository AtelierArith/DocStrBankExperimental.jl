```julia
logjac_forwarddiff(f, x; handleNaN, chunk, cfg)

```

Calculate the log Jacobian determinant of `f` at `x` using `ForwardDiff`.

# Note

`f` should be a bijection, mapping from vectors of real numbers to vectors of equal length.

When `handleNaN = true` (the default), `NaN` log Jacobians are converted to `-Inf`.
