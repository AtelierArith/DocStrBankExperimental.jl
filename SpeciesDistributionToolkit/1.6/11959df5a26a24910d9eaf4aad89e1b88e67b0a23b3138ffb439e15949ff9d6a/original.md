```
SDeMo.SDM(::Type{TF}, ::Type{CF}, predictors::Vector{SDMLayer{T}}, presences::SDMLayer{Bool}, absences::SDMLayer{Bool}) where {TF <: Transformer, CF <: Classifier, T <: Number}
```

Returns a SDM based on an array of predictors, a boolean layer of presences, and a boolean layer of absences.
