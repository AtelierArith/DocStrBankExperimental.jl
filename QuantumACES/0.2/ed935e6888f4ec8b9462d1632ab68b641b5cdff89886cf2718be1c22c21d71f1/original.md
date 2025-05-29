```
calc_merit(d::Design; warning::Bool = true)
calc_merit(d_rand::RandDesign; warning::Bool = true)
```

Returns a [`Merit`](@ref) object corresponding to the design `d` or randomised design `d_rand`, displaying a warning if the design does not have full covariance matrix data and `warning` is `true`.
