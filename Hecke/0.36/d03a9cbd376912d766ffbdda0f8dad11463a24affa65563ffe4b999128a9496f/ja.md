```
is_on_curve(E::EllipticCurve, coords::Vector) -> Bool
```

`coords` が $E$ 上の点を定義する場合は true を返し、そうでない場合は false を返します。配列 `coords` の長さは 2 でなければなりません。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> is_on_curve(E, [1, -2])
true

julia> is_on_curve(E, [1, -1])
false
```
