```julia
struct AndrewsRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

アンドリューズの重み付けは、残差に対応します。

$$
ρ(z) = -cos(πz/δ)/(π/δ)²
$$

ただし `|z|≤δ` の場合、そうでなければ `ρ(δ)` です。

注：対称的な重み付け。
