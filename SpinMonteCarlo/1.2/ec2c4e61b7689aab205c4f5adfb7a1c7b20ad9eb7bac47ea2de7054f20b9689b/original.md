```
gen_snapshot!(model, T, [N=1])
```

generate and return `N` snapshots (spin configuration).

# Arguments

  * `model::Model` : model
  * `T::Real` : temperature
  * `N::Integer=1` : the number of snapshots to be generated
  * `MCS::Integer=8192` : the number of Monte Carlo steps followed by snapshot generation
