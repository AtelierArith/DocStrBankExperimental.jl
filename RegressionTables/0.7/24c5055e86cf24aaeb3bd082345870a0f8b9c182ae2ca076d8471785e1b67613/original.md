```
struct StdError <: AbstractUnderStatistic
    val::Float64
end
StdError(rr::RegressionModel, k::Int; standardize=false, vargs...)
```

The standard error of a coefficient.
