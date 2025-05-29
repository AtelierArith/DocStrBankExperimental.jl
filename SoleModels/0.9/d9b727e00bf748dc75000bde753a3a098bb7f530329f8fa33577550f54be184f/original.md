```
struct DecisionTree{O} <: AbstractModel{O}
    root::M where {M<:Union{LeafModel{O},Branch{O}}}
    info::NamedTuple
end
```

[`DecisionTree`](@ref) wraps a constrained sub-tree of [`Branch`](@ref) and [`LeafModel`](@ref).

In other words, a [`DecisionTree`](@ref) is a symbolic model that operates as a nested structure of IF-THEN-ELSE blocks:

```
IF (antecedent_1) THEN
    IF (antecedent_2) THEN
        (consequent_1)
    ELSE
        (consequent_2)
    END
ELSE
    IF (antecedent_3) THEN
        (consequent_3)
    ELSE
        (consequent_4)
    END
END
```

where the [`antecedent`](@ref)s are formulas to be, and the [`consequent`](@ref)s are the feasible local outcomes of the block.

!!!note     Note that this structure also includes an `info::NamedTuple` for storing additional     information.

See also [`Branch`](@ref), [`DecisionList`](@ref), [`DecisionForest`](@ref), [`LeafModel`](@ref), [`MixedModel`](@ref).
