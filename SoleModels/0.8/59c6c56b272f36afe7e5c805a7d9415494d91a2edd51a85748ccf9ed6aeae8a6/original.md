A `DecisionTree` is a symbolic model that operates as a nested structure of IF-THEN-ELSE blocks:

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

where the antecedents are formulas to be, and the consequents are the feasible local outcomes of the block.

In practice, a `DecisionTree` simply wraps a constrained sub-tree of `Branch` and `LeafModel`:

```
struct DecisionTree{O} <: AbstractModel{O}
    root::M where {M<:AbstractModel}
    info::NamedTuple
end
```

Note that this structure also includes an `info::NamedTuple` for storing additional information.

See also [`MixedModel`](@ref), [`DecisionList`](@ref).
