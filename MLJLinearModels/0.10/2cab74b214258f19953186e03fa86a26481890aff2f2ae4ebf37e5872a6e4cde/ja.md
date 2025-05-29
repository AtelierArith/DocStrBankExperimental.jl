```julia
struct FairRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

残差の公正な重み付けは次のように対応します。

$$
ρ(z) = δ² (|z|/δ - log(1+|z|/δ))
$$

注：対称的な重み付け。
