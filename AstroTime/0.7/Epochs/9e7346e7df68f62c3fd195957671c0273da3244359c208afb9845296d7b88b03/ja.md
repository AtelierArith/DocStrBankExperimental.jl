```
getoffset(TCB, TDB, second, fraction)
```

現在のエポック（J2000以降の`second`と`fraction`）に対する[`TCB`](@ref)と[`TDB`](@ref)の間の線形オフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TCB, TDB, 0, 0.0)
-11.253721593757295
```
