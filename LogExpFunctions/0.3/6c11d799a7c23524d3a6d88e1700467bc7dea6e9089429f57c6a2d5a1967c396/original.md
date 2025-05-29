```julia
log1pmx(x)

```

Return `log(1 + x) - x`.

Use naive calculation or range reduction outside kernel range.  Accurate ~2ulps for all `x`. This will fall back to the naive calculation for argument types different from `Float64`.
