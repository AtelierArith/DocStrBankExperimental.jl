```
    atkinsonstalactiteplot(setting, iters, crit)
```

Runs the atkinson94 algorithm and additionally plots the Stalactite text plot as described in the paper. Works for data with less than  100 points at the moment (since screen width of 80-120 is the standard). See `atkinson94` for details.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `iters::Int`: Number of random samples.
  * `crit::Float64`: Critical value for residuals

# References

Atkinson, Anthony C. "Fast very robust methods for the detection of multiple outliers." Journal of the American Statistical Association 89.428 (1994): 1329-1339.
