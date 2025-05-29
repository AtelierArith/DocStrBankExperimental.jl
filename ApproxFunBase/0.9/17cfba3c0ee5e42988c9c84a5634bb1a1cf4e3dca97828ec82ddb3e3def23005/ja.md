```
Derivative()
```

未設定の空間での最初の導関数を返します。空間は演算子を適用または操作する際に推測されます。

# 例

```jldoctest
julia> Derivative() * Fun(x->x^2) ≈ Fun(x->2x)
true
```
