```
QuadraticOTNewton(;θ = 0.1, κ = 0.5, δ = 1e-5, armijo_max = 50)
```

アーミホパラメータ `θ` と `κ` を持つ半滑らかなニュートン法（Lorenz et al. 2019 のアルゴリズム 2）と共役勾配正則化 `δ`。 `armijo_max` はアーミホステップサイズの試行の最大数を設定します。

参照: [`QuadraticOTNewton`](@ref), [`quadreg`](@ref)
