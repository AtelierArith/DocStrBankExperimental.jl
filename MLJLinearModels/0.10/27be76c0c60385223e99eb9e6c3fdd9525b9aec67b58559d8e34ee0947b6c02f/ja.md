```julia
struct TalwarRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

タルワール重み付けは、次の残差に対応します。

$$
ρ(z) = z²/2
$$

もし `|z|≤δ` の場合、そうでなければ $ρ(z)=ρ(δ)$ です。

注：対称重み付け。
