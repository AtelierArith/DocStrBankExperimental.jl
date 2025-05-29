```
update_density_parameter(node::Node, species::Type{<:Species}, ::Type{T}; new_param_value::Float64) where T <: LifeStage
```

Update the parameterization of the density dependence model for `LifeStage` of `Species` in `Node`.
