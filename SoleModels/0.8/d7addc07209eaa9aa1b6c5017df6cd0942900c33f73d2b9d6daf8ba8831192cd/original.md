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

where the antecedents are formulas to be, and the consequents are the feasible local outcomes of the block. Using the classical semantics, the antecedents are evaluated in order, and a consequent is returned as soon as a valid antecedent is found, or when the computation reaches the ELSE clause.

See also [`Rule`](@ref), [`DecisionTree`](@ref), [`AbstractModel`](@ref).
