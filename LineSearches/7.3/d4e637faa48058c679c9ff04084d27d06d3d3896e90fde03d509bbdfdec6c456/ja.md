```
(ls::StrongWolfe)(df, x::AbstractArray, p::AbstractArray, alpha0::Real, x_new, ϕ_0, dϕ_0) -> alpha, ϕalpha
```

微分可能な関数 `df`（`NLSolversBase.OnceDifferentiable` または `NLSolversBase.TwiceDifferentiable` の意味で）、多次元の出発点 `x` とステップ `p`、およびステップ長の推定値 `alpha0` が与えられたとき、強いウルフ条件を満たす `alpha` を見つけます。

追加の詳細については、一次元のメソッドを参照してください。
