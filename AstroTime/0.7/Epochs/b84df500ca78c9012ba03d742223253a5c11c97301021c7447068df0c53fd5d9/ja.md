```
getoffset(TAI, TT, args...)
```

[`TAI`](@ref)と[`TT`](@ref)の間の固定オフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TAI, TT)
32.184
```
