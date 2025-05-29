```
update_mortality(node::Node, species::Type{<:Species}, life_stage::Type{<:LifeStage}, new_μ)
```

Update the temperature-sensitive mortality (`μ_temperature_response`) for the `LifeStage` of `Species` in `Node.`
