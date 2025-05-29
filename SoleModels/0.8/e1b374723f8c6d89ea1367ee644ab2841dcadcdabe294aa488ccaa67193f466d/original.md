```
antecedent(m::Union{Rule,Branch})::Formula
```

Return the antecedent of a rule/branch, that is, the formula to be checked upon applying the model.

See also [`apply`](@ref), [`consequent`](@ref), [`checkantecedent`](@ref), [`Rule`](@ref), [`Branch`](@ref).
