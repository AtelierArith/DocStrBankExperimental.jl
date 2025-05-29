```
fit_templates(models::AbstractMatrix{S},
              data::AbstractVector{<:Number};
              x0::AbstractVector{<:Number} = ones(S,length(models)),
              kws...) where S <: Number
```

This call signature supports the flattened formats for `models` and `data`. See the notes for the flattened call signature of [`StarFormationHistories.composite!`](@ref) for more details.
