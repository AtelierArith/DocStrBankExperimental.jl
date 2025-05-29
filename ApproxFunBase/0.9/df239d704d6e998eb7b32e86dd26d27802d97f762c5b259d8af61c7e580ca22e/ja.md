```
Derivative(k)
```

`k`-階導関数を、未設定の空間に作用させて返します。空間は演算子を適用または操作する際に推測されます。`k`が`Int`の場合、これは単変数空間における導関数を返します。`k`が`AbstractVector{Int}`の場合、これは多変数空間における偏導関数を返します。

# 例

```jldoctest
julia> Derivative(1) * Fun(x->x^2) ≈ Fun(x->2x)
true

julia> Derivative([0,1]) * Fun((x,y)->x^2+y^2) ≈ Fun((x,y)->2y)
true
```
