```
tstbit(x::Real, i::Integer) -> Bool
```

[`bit`](@ref)に似ていますが、位置`i`のビットを`Bool`として返します。

# 例

```jldoctest
julia> tstbit(0b101, 3)
true
```
