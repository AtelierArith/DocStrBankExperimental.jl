```
elem_type(parent)
elem_type(parent_type)
```

親オブジェクト（またはその型）を与えると、その要素の型を返します。

# 例

```jldoctest
julia> S, x = power_series_ring(QQ, 2, :x)
(Univariate power series ring over rationals, x + O(x^3))

julia> elem_type(S) == typeof(x)
true
```
