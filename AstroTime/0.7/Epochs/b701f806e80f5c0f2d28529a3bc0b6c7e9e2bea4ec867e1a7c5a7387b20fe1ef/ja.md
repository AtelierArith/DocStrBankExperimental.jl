```
getoffset(TCG, TT, second, fraction)
```

現在のエポック（J2000以降の`second`と`fraction`）に対する[`TCG`](@ref)と[`TT`](@ref)の間の線形オフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TCG, TT, 0, 0.0)
-0.5058332856685995
```
