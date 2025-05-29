```
posconsequent(m::Branch)::AbstractModel
```

Return the positive consequent of a branch, that is, the model to be applied if the [`antecedent`](@ref) evaluates to `true`.

See also [`antecedent`](@ref), [`Branch`](@ref), [`negconsequent`](@ref).
