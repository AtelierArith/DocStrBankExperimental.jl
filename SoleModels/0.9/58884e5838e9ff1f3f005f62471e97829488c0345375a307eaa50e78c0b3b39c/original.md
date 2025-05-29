```
negconsequent(m::Branch)::AbstractModel
```

Return the negative [`consequent`](@ref) of a branch; that is, the model to be applied if the antecedent evaluates to `false`.

See also [`antecedent`](@ref), [`Branch`](@ref), [`posconsequent`](@ref).
