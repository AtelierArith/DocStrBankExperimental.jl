```
Bool <: Integer
```

Boolean type, containing the values `true` and `false`.

`Bool` is a kind of number: `false` is numerically equal to `0` and `true` is numerically equal to `1`. Moreover, `false` acts as a multiplicative "strong zero":

```jldoctest
julia> false == 0
true

julia> true == 1
true

julia> 0 * NaN
NaN

julia> false * NaN
0.0
```

See also: [`digits`](@ref), [`iszero`](@ref), [`NaN`](@ref).
