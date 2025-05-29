```
Type_IOP(n::Integer, nc::Integer [, a [; nam="" [; msg=true]]])
```

`BigInt` if `n` is a `BigInt` or `n > nc`, otherwise `Int`; `a` is an  auxiliary second variable.

  * `nam` : function name
  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Examples:

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
