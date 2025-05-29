```julia
struct LogisticRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

残差のロジスティック重み付けは次の式に対応します。

$$
ρ(z) = δ² log(cosh(z/δ))
$$

注：対称重み付け。
