```
antecedent(m::Union{Rule,Branch})::Formula
```

Return the antecedent of a [`Rule`](@ref) or a [`Branch`](@ref), that is, the formula to be checked upon applying the model.

See also [`apply`](@ref), [`Branch`](@ref), [`checkantecedent`](@ref), [`consequent`](@ref), [`Rule`](@ref).
