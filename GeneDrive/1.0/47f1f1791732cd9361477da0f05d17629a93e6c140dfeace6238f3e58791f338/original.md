```
update_density_model(node::Node, species::Type{<:Species}, ::Type{T}; new_density_model::Density) where T <: LifeStage
```

Update the functional form of the density dependence model for `LifeStage` of `Species` in `Node`.
