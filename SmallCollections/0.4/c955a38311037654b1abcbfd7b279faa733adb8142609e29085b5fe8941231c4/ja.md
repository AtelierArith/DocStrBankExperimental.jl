```
delete(d::AbstractSmallDict{N,K,V}, key) where {N,K,V} -> SmallDict{N,K,V}
```

`key` に対するマッピングを `d` から削除し（存在する場合）、新しい辞書を返します。

また、`Base.delete!`、[`pop`](@ref pop(::AbstractSmallDict, ::Any)) も参照してください。
