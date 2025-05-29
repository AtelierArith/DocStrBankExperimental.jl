A `MixedModel` is a symbolic model that operaters as a free nested structure of IF-THEN-ELSE and IF-ELSEIF-ELSE blocks:

```
IF (antecedent_1) THEN
    IF (antecedent_1)     THEN (consequent_1)
    ELSEIF (antecedent_2) THEN (consequent_2)
    ELSE (consequent_1_default) END
ELSE
    IF (antecedent_3) THEN
        (consequent_3)
    ELSE
        (consequent_4)
    END
END
```

where the antecedents are formulas to be checked, and the consequents are the feasible local outcomes of the block.

In Sole.jl, this logic can implemented using `AbstractModel`s such as `Rule`s, `Branch`s, `DecisionList`s, `DecisionTree`s, and the be wrapped into a `MixedModel`:

```
struct MixedModel{O,FM<:AbstractModel} <: AbstractModel{O}
    root::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

Note that `FM` refers to the Feasible Models (`FM`) allowed in the model's sub-tree.

See also [`DecisionTree`](@ref), [`DecisionList`](@ref).
