```
hash256(x::Block) -> Vector{UInt8}
hash256(x::Header) -> Vector{UInt8}
hash256(x::Tx) -> Vector{UInt8}
```

`Block`、`Header`、または`Tx`のシリアル化の逆順のダブルsha256を返します。`Tx`は常にレガシー取引としてシリアル化されます。

```julia
hash256(block)
hash256(header)
hash256(transaction)
```
