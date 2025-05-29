```
struct DecisionList{O} <: AbstractModel{O}
    rulebase::Vector{Rule{_O} where {_O<:O}}
    defaultconsequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

A `DecisionList` (or *decision table*, or *rule-based model*) is a symbolic model that has the semantics of an IF-ELSEIF-ELSE block:

```
IF (antecedent_1)     THEN (consequent_1)
ELSEIF (antecedent_2) THEN (consequent_2)
...
ELSEIF (antecedent_n) THEN (consequent_n)
ELSE (consequent_default) END
```

where the [`antecedent`](@ref)s are formulas to be, and the [`consequent`](@ref)s are the feasible local outcomes of the block.

Using the classical semantics, the [`antecedent`](@ref)s are evaluated in order, and a [`consequent`](@ref) is returned as soon as a valid antecedent is found, or when the computation reaches the ELSE clause.

See also [`AbstractModel`](@ref), [`DecisionTree`](@ref), [`Rule`](@ref).
