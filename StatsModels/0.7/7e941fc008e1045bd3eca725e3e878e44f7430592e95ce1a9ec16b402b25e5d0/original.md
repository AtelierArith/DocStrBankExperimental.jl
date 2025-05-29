```
setcontrasts!(mf::ModelFrame; kwargs...)
setcontrasts!(mf::ModelFrame, contrasts::Dict{Symbol})
```

Update the contrasts used for coding categorical variables in [`ModelFrame`](@ref) in place.  This is accomplished by computing a new schema based on the provided contrasts and the `ModelFrame`'s data, and applying it to the `ModelFrame`'s `FormulaTerm`.

Note that only the `ModelFrame` itself is mutated: because `AbstractTerm`s are immutable, any changes will produce a copy.
