```
hs93initialset(setting)
```

Perform the Hadi & Simonoff (1993) algorithm's first part for a given regression setting. The returned array of indices are indices of clean subset length of p + 1 where p is the number of regression parameters.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> hs93initialset(reg0001)
3-element Array{Int64,1}:
 4
 3
 5
```

# References

Hadi, Ali S., and Jeffrey S. Simonoff. "Procedures for the identification of  multiple outliers in linear models." Journal of the American Statistical  Association 88.424 (1993): 1264-1272.
