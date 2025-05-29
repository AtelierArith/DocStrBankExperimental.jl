```
quo(::Type{Field}, R::Ring, a::RingElement; cached::Bool = true)
```

`S, f` を返します。ここで、`S = residue_field(R, a)` であり、`f` は `R` から `S` への射影写像です。この写像は、剰余体の要素を環 `R` に戻すリフトとしてのセクションを持つ写像として提供されます。
