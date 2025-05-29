```
struct TStat <: AbstractUnderStatistic
    val::Float64
end
TStat(rr::RegressionModel, k::Int; vargs...)
```

係数のt統計量。
