krichevskii_parameter(model::EoSModel, T, crit = nothing)

krichevskiiパラメータを計算します。これは次のように定義されます：

```
∂p/∂x₂ |T → Tc₁,V → Vc₁, x₂ → 0
```

ここで、最初の成分は溶媒で、2番目は溶質です。
