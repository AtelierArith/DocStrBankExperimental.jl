```
conditionalType(n::T, nc::T [; msg=true]) where T<:Integer
```

`n > nc` の場合、型 `T` を `BigInt` に変換します。

#### 例:

```
julia> conditionalType(46, 46)
Int64

julia> conditionalType(47, 46)
BigInt
```
