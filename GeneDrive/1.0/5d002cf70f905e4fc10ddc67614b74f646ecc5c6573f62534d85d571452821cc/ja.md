```
update_mortality(node::Node, species::Type{<:Species}, life_stage::Type{<:LifeStage}, new_μ)
```

`Node`内の`Species`の`LifeStage`に対する温度感受性の死亡率（`μ_temperature_response`）を更新します。
