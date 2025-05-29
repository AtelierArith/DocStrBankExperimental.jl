```
struct TStat <: AbstractUnderStatistic
    val::Float64
end
TStat(rr::RegressionModel, k::Int; vargs...)
```

The t-statistic of a coefficient.
