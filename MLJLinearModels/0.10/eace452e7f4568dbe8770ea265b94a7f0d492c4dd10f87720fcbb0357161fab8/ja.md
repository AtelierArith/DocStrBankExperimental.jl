```julia
struct QuantileRho{δ} <: MLJLinearModels.RobustRho1P{δ}
```

分位数回帰の残差に対する重み付けは次のようになります

$$
ρ(z) = -z(δ - 1(z>=0))
$$

注: 非対称重み付け、"-" の符号は、quantregのような類似のライブラリが残差を `y-Xθ` と定義するのに対し、私たちはその逆を行うため（勾配などの便宜のため）です。
