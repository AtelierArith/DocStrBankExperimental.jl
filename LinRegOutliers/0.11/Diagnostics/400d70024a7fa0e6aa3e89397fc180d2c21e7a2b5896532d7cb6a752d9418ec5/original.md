```
cooksoutliers(setting; alpha = 0.5)
```

Calculates Cooks distance for a given regression setting and reports the potentials outliers

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `alpha::Float`: Probability for cutoff value. quantile(Fdist(p, n-p), alpha) is used for cutoff. Default is 0.5.

# Output

  * `["distance"]`: Cooks distances.
  * `["cutoff"]`: Quantile of the F distribution.
  * `["potentials"]`: Vector of indices of potential regression outliers.
