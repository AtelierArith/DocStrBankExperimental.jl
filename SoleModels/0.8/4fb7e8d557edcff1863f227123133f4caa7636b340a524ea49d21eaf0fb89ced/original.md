```
struct Rule{O} <: AbstractModel{O}
    antecedent::Formula
    consequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

A `Rule` is one of the fundamental building blocks of symbolic modeling, and has the semantics:

```
IF (antecedent) THEN (consequent) END
```

where the antecedent is a formula to be checked, and the consequent is the local outcome of the block.

See also [`antecedent`](@ref), [`consequent`](@ref), [`SoleLogics.Formula`](@ref), [`AbstractModel`](@ref).
