```
FitCauchy(b=500)
```

コーシー分布の近似パラメータ推定。推定は近似された分位数に基づいています。分布の推定方法の詳細については、[`Quantile`](@ref)および[`ExpandingHist`](@ref)を参照してください。

# 例

```
o = fit!(FitCauchy(), randn(1000))
```
