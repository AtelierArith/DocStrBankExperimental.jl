```
jacknifedS(setting, k)
```

Estimate standard error of regression with the kth observation is dropped.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `k::Int`: Index of the omitted observation.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> jacknifedS(reg, 2)
57.518441664761035

julia> jacknifedS(reg, 15)
56.14810222161477
```
