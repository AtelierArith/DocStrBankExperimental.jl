```
get_circle_residual(F::Function, z::InvariantCircle, Nθ::Integer)
```

p個の不変円の連鎖のKAMのような残差を取得します。

> Rᵢ₁ = z₁(θᵢ+τ) - F(z_p(θᵢ))   Rᵢⱼ = zⱼ(θᵢ) - F(zⱼ₋₁(θᵢ)) ただし 2<=j<=p


引数:

  * `F`: シンプレクティック写像
  * `z`: 不変円
  * `Nθ`: 残差が取られるθ点の数
