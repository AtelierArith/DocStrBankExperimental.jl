```
popfirst(v::V) where {T, V <: AbstractCapacityVector{T}} -> Tuple{V,T}
```

タプル `(w, x)` を返します。ここで `x` は `v` の最初の要素であり、`w` はこの要素を削除した `v` から得られます。ベクトル `v` は空であってはなりません。

`Base.popfirst!`、`BangBang.popfirst!!` も参照してください。
