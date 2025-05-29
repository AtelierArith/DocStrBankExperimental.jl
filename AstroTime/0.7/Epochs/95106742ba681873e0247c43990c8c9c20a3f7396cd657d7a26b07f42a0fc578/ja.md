```
getoffset(UT1, TAI, second, fraction[, eop])
```

現在のエポック（J2000からの`second`および`fraction`）に対する[`UT1`](@ref)と[`TAI`](@ref)のオフセットを秒単位で返します。オプションで、カスタムの地球回転データ構造`eop`を提供することができます。詳細は[EarthOrientation.jl](https://github.com/JuliaAstro/EarthOrientation.jl)を参照してください。

# 例

```jldoctest; setup = :(using AstroTime; AstroTime.load_test_eop())
julia> getoffset(UT1, TAI, 0, 0.0)
31.644974965344606
```
