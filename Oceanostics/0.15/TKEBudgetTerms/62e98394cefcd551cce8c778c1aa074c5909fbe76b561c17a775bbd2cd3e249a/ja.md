```julia
KineticEnergyDissipationRate(model; U, V, W, location)

```

運動エネルギー散逸率を計算します。定義は次のとおりです。

```
ε = ν (∂uᵢ/∂xⱼ) (∂uᵢ/∂xⱼ)
ε = ∂ⱼuᵢ ⋅ Fᵢⱼ
```

ここで、∂ⱼuᵢは速度勾配テンソル、Fᵢⱼは応力テンソルです。
