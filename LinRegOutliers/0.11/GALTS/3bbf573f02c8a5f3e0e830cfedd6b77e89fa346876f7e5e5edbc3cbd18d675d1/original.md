```
galts(setting)
```

Perform Satman(2012) algorithm for estimating LTS coefficients.

# Arguments

  * `setting`: A regression setting object.

# Description

The algorithm performs a genetic search for estimating LTS coefficients using C-Steps. 

# Output

  * `["betas"]`: Robust regression coefficients
  * `["best.subset"]`: Clean subset of h observations, where h is an integer greater than n / 2. The default value of h is `Int(floor((n + p + 1.0) / 2.0))`.
  * `["objective"]`: Objective value

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> galts(reg)
Dict{Any,Any} with 3 entries:
  "betas"       => [-56.5219, 1.16488]
  "best.subset" => [3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 23, 24]
  "objective"   => 3.43133
```

# References

Satman, M. Hakan. "A genetic algorithm based modification on the lts algorithm for large data sets."  Communications in Statistics-Simulation and Computation 41.5 (2012): 644-652.
