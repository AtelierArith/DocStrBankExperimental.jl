```
struct StdError <: AbstractUnderStatistic
    val::Float64
end
StdError(rr::RegressionModel, k::Int; standardize=false, vargs...)
```

係数の標準誤差。
