```
getoffset(TAI, UT1, second, fraction[, eop])
```

[`TAI`](@ref) と [`UT1`](@ref) のオフセットを現在のエポック（J2000 からの `second` と `fraction`）に対して秒単位で返します。オプションで、カスタムの地球回転データ構造 `eop` を提供することができます。詳細は [EarthOrientation.jl](https://github.com/JuliaAstro/EarthOrientation.jl) を参照してください。

# 例

```jldoctest; setup = :(using AstroTime; AstroTime.load_test_eop())
julia> getoffset(TAI, UT1, 0, 0.0)
-31.644974644349812
```
