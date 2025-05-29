```
getoffset(TT, TCG, second, fraction)
```

現在のエポック（J2000以降の`second`と`fraction`）に対する[`TT`](@ref)と[`TCG`](@ref)の間の線形オフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TT, TCG, 0, 0.0)
0.5058332860211293
```
