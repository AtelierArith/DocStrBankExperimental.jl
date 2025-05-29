```julia
PlanarEntrySystem(; name, defaults, kwargs...)

```

大気圏突入のための `ModelingToolkit.ODESystem` です。現在、提供されているのは指数大気モデルのみです！出力モデルは `Memoize.jl` でキャッシュされます。惑星特有のパラメータは地球の値がデフォルトです。

状態の順序は次の通りです: `[γ, v, r, θ]`。

パラメータの順序は次の通りです: `[R, P, H, m, A, C, μ]`。

# 拡張ヘルプ

このモデルは、球状の惑星の上空で物体が指数大気を通過する方法を説明します。

### 使用法

```julia
model = PlanarEntrySystem()
```
