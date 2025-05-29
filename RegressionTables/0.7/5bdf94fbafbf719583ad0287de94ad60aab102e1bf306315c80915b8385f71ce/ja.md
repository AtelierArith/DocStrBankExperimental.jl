```
struct ConfInt <: AbstractUnderStatistic
    val::Tuple{Float64, Float64}
end
ConfInt(rr::RegressionModel, k::Int; level=0.95, standardize=false, vargs...)
```

係数の信頼区間。デフォルトの信頼水準は95%です（`RegressionTable.default_confint_level(render::AbstractRenderType, rr) = 0.90`などを設定することで変更可能です）。
