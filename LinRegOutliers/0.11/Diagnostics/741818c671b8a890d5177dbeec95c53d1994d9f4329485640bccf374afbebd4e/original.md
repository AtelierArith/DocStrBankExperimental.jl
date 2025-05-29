```
dffit(setting, i)
```

Calculate the effect of the ith observation on the linear regression fit.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `i::Int`: Index of the observation.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> dffit(reg, 1)
2.3008326745719785

julia> dffit(reg, 15)
2.7880619386124295

julia> dffit(reg, 16)
3.1116532421969794

julia> dffit(reg, 17)
4.367981450347031

julia> dffit(reg, 21)
-5.81610150322166
```

# References

Belsley, David A., Edwin Kuh, and Roy E. Welsch. Regression diagnostics:  Identifying influential data and sources of collinearity. Vol. 571. John Wiley & Sons, 2005.
