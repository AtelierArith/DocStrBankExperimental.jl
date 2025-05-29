```julia
struct BisquareRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

残差に対するビスクエア重み付けは次のようになります。

$$
ρ(z) = δ²/6 (1-(1-(z/δ)²)³)
$$

ただし `|z|≤δ` の場合、そうでなければ `δ²/6` です。

注：対称重み付け。
