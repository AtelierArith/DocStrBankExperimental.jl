```
getoffset(TT, TAI, args...)
```

[`TT`](@ref) と [`TAI`](@ref) の間の固定オフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TT, TAI)
-32.184
```
