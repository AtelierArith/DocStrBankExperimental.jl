```
opex_var(n::Node)
opex_var(n::Node, t)
```

ノード `n` の変数 OPEX を `TimeProfile` として、または運用期間 `t` で返します。

!!! warning "ストレージノード"
    変数 OPEX は [`Storage`](@ref) ノードに対して直接定義されていません。代わりに、該当するフィールドで関数を呼び出す必要があります。詳細は [`opex_var(stor_par::AbstractStorageParameters)`](@ref) を参照してください。

