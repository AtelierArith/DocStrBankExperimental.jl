```
update_density!(node::Node, species::Type{<:Species}, ::Type{T}; new_density::Density) where T <: LifeStage
```

`Node`内の`Species`の`LifeStage`の密度依存モデルの機能的形式とパラメータ化の両方を更新します。
