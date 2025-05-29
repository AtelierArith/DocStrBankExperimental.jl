```
update_duration(node::Node, species::Type{<:Species}, life_stage::Type{<:LifeStage}, new_q)
```

`Node`内の`Species`の`LifeStage`に対する温度感受性の期間（`q_temperature_response`）を更新します。
