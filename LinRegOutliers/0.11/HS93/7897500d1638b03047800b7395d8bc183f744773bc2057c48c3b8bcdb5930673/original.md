```
hs93basicsubset(setting, initialindices)
```

Perform the Hadi & Simonoff (1993) algorithm's second part for a given regression setting. The returned array of indices are indices of clean subset of length h where h is at least the half of the number of observations. h is set to  integer part of (n + p - 1) / 2.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `initialindices::Array{Int, 1}`: (p + 1) subset of clean observations.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> initialsetindices = hs93initialset(reg0001)
3-element Array{Int64,1}:
 4
 3
 5
 julia> hs93basicsubset(reg0001, initialsetindices)
12-element Array{Int64,1}:
  5
  9
 10
  3
  6
  4
  7
 22
 11
  8
 12
 13
```

# References

Hadi, Ali S., and Jeffrey S. Simonoff. "Procedures for the identification of  multiple outliers in linear models." Journal of the American Statistical  Association 88.424 (1993): 1264-1272.
