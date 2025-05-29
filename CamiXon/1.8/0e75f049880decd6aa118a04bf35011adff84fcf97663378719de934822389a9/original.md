```
conditionalType(n::T, nc::T [; msg=true]) where T<:Integer
```

Convert type `T` to `BigInt` for `n > nc`.

#### Example:

```
julia> conditionalType(46, 46)
Int64

julia> conditionalType(47, 46)
BigInt
```
