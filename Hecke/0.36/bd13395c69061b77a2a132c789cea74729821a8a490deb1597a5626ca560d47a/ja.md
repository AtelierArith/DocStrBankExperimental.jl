```
absolute_value(x::NumFieldElem, p::InfPlc, prec::Int = 32) -> ArbFieldElem
```

無限位に含まれる正規化された絶対評価における `x` の評価を返します。もし `e` が `p` を誘導する複素埋め込みであれば、`e` が実数の場合は `abs(e(x))`、そうでなければ `abs(e(x))^2` です。

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field(x^3 - 2, "a");

julia> absolute_value(a, real_places(K)[1])
[1.2599210499 +/- 8.44e-11]

julia> absolute_value(a, complex_places(K)[1])
[1.587401052 +/- 6.63e-10]
```
