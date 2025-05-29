```
capacity(n::Node)
capacity(n::Node, t)
```

ノード `n` の容量を `TimeProfile` として、または運用期間 `t` で返します。

!!! warning "ストレージノード"
    [`Storage`](@ref) ノードに対しては、容量が直接定義されていません。代わりに、該当するフィールドで関数を呼び出す必要があります。詳細は [`capacity(stor_par::AbstractStorageParameters)`](@ref) を参照してください。

