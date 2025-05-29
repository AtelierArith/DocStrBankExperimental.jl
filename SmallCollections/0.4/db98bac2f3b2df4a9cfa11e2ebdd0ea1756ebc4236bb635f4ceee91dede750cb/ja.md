```
popat(v::V, i::Integer) where {T, V <: AbstractCapacityVector{T}} -> Tuple{V,T}
```

タプル `(w, x)` を返します。ここで `w` は `v` から位置 `i` で要素 `x` を削除することによって得られます。後者は `1` と `length(v)` の間でなければなりません。

`Base.popat!`、`BangBang.popat!!` も参照してください。
