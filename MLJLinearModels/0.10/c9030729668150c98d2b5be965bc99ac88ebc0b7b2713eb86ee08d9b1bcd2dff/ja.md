```julia
struct HuberRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

残差に対するHuber重み付けは次のように対応します。

$$
ρ(z) = z²/2
$$

もし `|z|≤δ` の場合、そして `ρ(z)=δ(|z|-δ/2)` それ以外の場合。

注：対称重み付け。
