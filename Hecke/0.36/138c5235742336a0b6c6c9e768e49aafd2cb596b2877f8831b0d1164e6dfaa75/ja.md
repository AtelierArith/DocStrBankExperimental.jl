```
is_on_curve(C::HypellCrv{T}, coords::Vector{T}) -> Bool
```

`coords` が $C$ 上の点を定義する場合は true を返し、それ以外の場合は false を返します。配列 `coords` の長さは 2 でなければなりません。
