```
update_density_model(node::Node, species::Type{<:Species}, ::Type{T}; new_density_model::Density) where T <: LifeStage
```

`Node`内の`Species`の`LifeStage`の密度依存モデルの関数形式を更新します。
