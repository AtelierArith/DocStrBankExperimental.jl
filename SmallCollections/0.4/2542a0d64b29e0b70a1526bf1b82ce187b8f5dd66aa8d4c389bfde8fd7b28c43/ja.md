```
delete(s::AbstractSmallSet{N,T}, x) where {N,T} -> SmallSet{N,T}
```

`s` から要素 `x` を削除し（存在する場合）、新しいセットを返します。

また、`Base.delete!`、[`pop`](@ref pop(::AbstractSmallSet, ::Any)) も参照してください。
