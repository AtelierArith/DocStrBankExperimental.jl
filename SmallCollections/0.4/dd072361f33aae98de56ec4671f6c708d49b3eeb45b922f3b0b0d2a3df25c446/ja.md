```
pop(v::V) where {T, V <: AbstractCapacityVector{T}} -> Tuple{V,T}
```

タプル `(w, x)` を返します。ここで `x` は `v` の最後の要素であり、`w` はこの要素を削除した `v` から得られます。ベクトル `v` は空であってはなりません。

また、`Base.pop!`、`BangBang.pop!!` も参照してください。
