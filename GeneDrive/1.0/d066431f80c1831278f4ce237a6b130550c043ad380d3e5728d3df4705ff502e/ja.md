```
get_mortality(node::Node, species::Type{<:Species}, life_stage::Type{<:LifeStage})
```

ノード内の種のライフステージに対する温度依存性死亡率（`μ_temperature_response`）を返します。
