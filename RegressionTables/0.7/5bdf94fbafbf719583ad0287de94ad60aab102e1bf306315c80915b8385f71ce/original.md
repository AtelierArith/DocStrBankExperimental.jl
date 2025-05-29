```
struct ConfInt <: AbstractUnderStatistic
    val::Tuple{Float64, Float64}
end
ConfInt(rr::RegressionModel, k::Int; level=0.95, standardize=false, vargs...)
```

The confidence interval of a coefficient. The default confidence level is 95% (can be changed by setting  `RegressionTable.default_confint_level(render::AbstractRenderType, rr) = 0.90` or similar).
