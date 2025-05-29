```
pop(s::AbstractSmallSet{N,T}) where {N,T} -> Tuple{SmallSet{N,T}, T}
```

要素 `x` を `s` から削除し、`x` とともに新しいセットを返します。セット `s` は空であってはなりません。

`Base.pop!` も参照してください。
