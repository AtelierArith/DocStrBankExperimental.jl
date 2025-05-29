```
get_previous_lifestage(node::Node, species::Type{<:Species}, ::Stage{T}) where T <: LifeStage
```

Show `LifeStage` dependency: return data for the `LifeStage` previous to the specified `LifeStage` of `Species` in `Node`.
