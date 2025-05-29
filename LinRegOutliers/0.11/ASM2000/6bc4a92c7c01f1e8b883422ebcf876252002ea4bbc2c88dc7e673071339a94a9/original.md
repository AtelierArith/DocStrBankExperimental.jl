```
asm2000(setting)
```

Perform the Setan, Halim and Mohd (2000) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Description

The algorithm performs a Least Trimmed Squares (LTS) estimate and yields standardized  residual - fitted response pairs. A single linkage clustering algorithm is performed on these pairs. Like `smr98`, the cluster tree is cut using the Majona criterion. Subtrees with  relatively small number of observations are declared to be outliers.

# Output

  * `["outliers"]`: Vector of indices of outliers.
  * `["betas"]`: Vector of regression coefficients.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> asm2000(reg0001)
Dict{Any, Any} with 2 entries:
  "betas"    => [-63.4816, 1.30406]
  "outliers" => [15, 16, 17, 18, 19, 20]
```

# References

Robiah Adnan, Mohd Nor Mohamad, & Halim Setan (2001).  Identifying multiple outliers in linear regression: robust fit and clustering approach.  Proceedings of the Malaysian Science and Technology Congress 2000: Symposium C, Vol VI, (p. 400).  Malaysia: Confederation of Scientific and Technological Associations in Malaysia COSTAM.
