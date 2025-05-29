```
restrict(p::InfPlc, K::NumField)
```

数体 `L` の無限位 `p` と、`L` の基底体として現れる数体 `K` が与えられたとき、`p` の `L` への制限を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(3);

julia> L, b = number_field(polynomial(K, [1, 0, 1]), "b");

julia> p = complex_places(L)[1];

julia> restrict(p, K)
Infinite place of
Real quadratic field defined by x^2 - 3
corresponding to
Complex embedding corresponding to -1.73 of K
```
