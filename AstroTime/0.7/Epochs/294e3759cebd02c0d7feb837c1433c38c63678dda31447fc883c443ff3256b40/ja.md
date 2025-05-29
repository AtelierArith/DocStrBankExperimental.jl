```
getoffset(TDB, TCB, second, fraction)
```

現在のエポック（J2000からの`second`と`fraction`）に対する[`TDB`](@ref)と[`TCB`](@ref)の間の線形オフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TDB, TCB, 0, 0.0)
11.253721768248475
```
