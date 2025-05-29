```
BasisFunctionApproximation(y::Vector, v, bfe::BasisFunctionExpansion, λ = 0)
```

パラメータ同定を行い、関数 `y = ϕ(v)` を特定します。ここで、`ϕ` はタイプ `bfe` の基底関数展開です。`λ` はオプションの正則化パラメータ（L²正則化）です。
