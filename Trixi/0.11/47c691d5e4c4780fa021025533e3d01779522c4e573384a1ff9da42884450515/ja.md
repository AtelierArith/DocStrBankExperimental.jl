```
flux(u, normal_direction::AbstractVector, equations::AbstractEquations{1})
```

非整数引数 `normal_direction` を持つ `flux` の呼び出しを可能にします。1次元方程式に対して、`flux(u, 1, equations)` の値を `normal_direction[1]` でスケーリングして返します。
