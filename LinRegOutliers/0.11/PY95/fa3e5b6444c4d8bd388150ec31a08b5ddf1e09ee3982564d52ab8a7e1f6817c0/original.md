```
py95(setting)
```

Perform the Pena & Yohai (1995) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Description

The algorithm starts by constructing an influence matrix using results  of an ordinary least squares estimate for a given model and data. In the second stage,  the eigen structure of the influence matrix is examined for detecting suspected subsets of data.

# Output

  * `["outliers"]`: Array of indices of outliers
  * `["suspected.sets"]`: Arrays of indices of observations for corresponding eigen value of the influence matrix.
  * `["betas]`: Vector of estimated regression coefficients using the clean observations.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(y ~ x1 + x2 + x3), hbk);
julia> py95(reg0001)
ict{Any,Any} with 2 entries:
  "outliers"       => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
  "suspected.sets" => Set([[14, 13], [43, 54, 24, 38, 22], [6, 10], [14, 7, 8, 3, 10, 2, 5, 6, 1, 9, 4…
```

# References

Peña, Daniel, and Victor J. Yohai. "The detection of influential subsets in linear  regression by using an influence matrix." Journal of the Royal Statistical Society:  Series B (Methodological) 57.1 (1995): 145-156.
