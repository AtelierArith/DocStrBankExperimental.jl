```
set_outplant_deployment!(
    name::String,
    reefset::String,
    max_effort::Int64,
    first_year::Int64,
    last_year::Int64,
    year_step::Int64,
    area_km2::Vector{Float64},
)::Nothing
```

年の範囲にわたって出植えデプロイメントを設定し、設定されたグリッドサイズを維持するためにサンゴのデプロイ密度を自動的に決定します。
