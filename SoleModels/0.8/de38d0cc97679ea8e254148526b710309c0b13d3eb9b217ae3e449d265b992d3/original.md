```
struct Branch{O} <: AbstractModel{O}
    antecedent::Formula
    posconsequent::M where {M<:AbstractModel{<:O}}
    negconsequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

A `Branch` is one of the fundamental building blocks of symbolic modeling, and has the semantics:

```
IF (antecedent) THEN (positive consequent) ELSE (negative consequent) END
```

where the antecedent is a formula to be checked and the consequents are the feasible local outcomes of the block. If checking the antecedent evaluates to the top of the algebra, then the positive consequent is applied; otherwise, the negative consequenti is applied.

See also [`antecedent`](@ref), [`posconsequent`](@ref), [`negconsequent`](@ref), [`SoleLogics.check`](@ref), [`SoleLogics.Formula`](@ref), [`Rule`](@ref), [`AbstractModel`](@ref).
