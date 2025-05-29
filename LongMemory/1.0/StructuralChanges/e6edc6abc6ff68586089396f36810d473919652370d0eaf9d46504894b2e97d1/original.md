```
lm_change_test(y::Array; uplim::Real = 0.15, lowlim::Real = 0.15)
```

Estimates the location of a structural change in a long memory model.

# Arguments

  * `y::Array`: The series to be tested.

# Optional arguments

  * `uplim::Real = 0.15`: The upper limit of the fraction of the series to be tested.
  * `lowlim::Real = 0.15`: The lower limit of the fraction of the series to be tested.

# Output

  * `τ::Int`: The estimated location of the structural change.

# Examples

```julia-repl
julia> lm_change_test(randn(100))
```

# Notes

The function estimates the location of a structural change in a long memory model. The function uses the Whittle estimator to estimate the long memory parameter. Then, it integrates the series and computes the t-statistics of the OLS regression of the integrated series on the starred series. The function computes the forward and backward t-statistics and returns the location of the maximum squared t-statistic. Hence, it is robust to the direction of the change.

# References

Martins and Rodrigues (2014), "Testing for persistence change in fractionally integrated models: An application to world inflation rates", Computational Statistics and Data Analysis, 76.
