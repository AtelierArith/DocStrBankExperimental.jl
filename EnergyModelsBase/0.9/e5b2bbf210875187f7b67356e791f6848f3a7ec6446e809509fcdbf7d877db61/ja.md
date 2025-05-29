```
opex_fixed(n::Node)
opex_fixed(n::Node, t_inv)
```

ノード `n` の固定OPEXを `TimeProfile` として、または戦略的期間 `t_inv` で返します。

!!! warning "ストレージノード"
    固定OPEXは [`Storage`](@ref) ノードに対して直接定義されていません。代わりに、該当するフィールドで関数を呼び出す必要があります。詳細は [`opex_fixed(stor_par::AbstractStorageParameters)`](@ref) を参照してください。

