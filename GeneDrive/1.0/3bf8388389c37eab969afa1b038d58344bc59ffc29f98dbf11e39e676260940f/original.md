```
update_density!(node::Node, species::Type{<:Species}, ::Type{T}; new_density::Density) where T <: LifeStage
```

Update both the functional form and parameterization of the density dependence model for `LifeStage` of `Species` in `Node`.
