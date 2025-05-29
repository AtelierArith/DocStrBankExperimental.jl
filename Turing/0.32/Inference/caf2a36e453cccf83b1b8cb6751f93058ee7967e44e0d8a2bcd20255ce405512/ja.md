```
HMC(ϵ::Float64, n_leapfrog::Int; adtype::ADTypes.AbstractADType = AutoForwardDiff())
```

静的軌道を持つハミルトニアンモンテカルロサンプラー。

# 引数

  * `ϵ`: 使用するリープフロッグステップサイズ。
  * `n_leapfrog`: 使用するリープフロッグステップの数。
  * `adtype`: 自動微分（AD）バックエンド。指定されていない場合は、`ForwardDiff`が使用され、その`chunksize`は自動的に決定されます。

# 使用法

```julia
HMC(0.05, 10)
```

# ヒント

`HMC`を使用しているときに勾配エラーが発生する場合は、リープフロッグステップサイズ`ϵ`を減らしてみてください。例えば：

```julia
# 元のステップサイズ
sample(gdemo([1.5, 2]), HMC(0.1, 10), 1000)

# 減少したステップサイズ
sample(gdemo([1.5, 2]), HMC(0.01, 10), 1000)
```
