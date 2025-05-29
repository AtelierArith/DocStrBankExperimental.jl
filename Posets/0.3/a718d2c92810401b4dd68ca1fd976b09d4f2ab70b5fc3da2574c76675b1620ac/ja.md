```
covered_by(p::Poset, a::Integer, b::Integer)::Bool
```

`a < b` が `p` において成り立ち、かつ `a < c < b` を満たす要素 `c` が存在しない場合、`true` を返します。
