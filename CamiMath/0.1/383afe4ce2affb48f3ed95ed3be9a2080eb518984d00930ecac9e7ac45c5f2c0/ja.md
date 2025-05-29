```
Type_IOP(n::Integer, nc::Integer [, a [; nam="" [; msg=true]]])
```

`BigInt` は `n` が `BigInt` の場合または `n > nc` の場合、それ以外は `Int`；`a` は補助的な第二変数です。

  * `nam` : 関数名
  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

#### 例:

```
julia> Type_IOP(1, 1)
Int64

julia> Type_IOP(big(1), 1)
BigInt

julia> Type_IOP(2, 1)
BigInt

julia> Type_IOP(1, 1; nam="test")
Int64

julia> Type_IOP(2, 1, 0; nam="test")
 IOP capture at test(2, 0): output converted to BigInt
BigInt
```
