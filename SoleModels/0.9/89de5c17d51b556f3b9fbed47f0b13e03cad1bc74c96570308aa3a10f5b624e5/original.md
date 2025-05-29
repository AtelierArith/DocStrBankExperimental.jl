```
struct MixedModel{O,FM<:AbstractModel} <: AbstractModel{O}
    root::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

A [`MixedModel`](@ref) is a wrapper of multiple [`AbstractModel`](@ref)s such as [`Rule`](@ref)s, [`Branch`](@ref)s, [`DecisionList`](@ref)s, [`DecisionTree`](@ref).

In other words, a [`MixedModel`](@ref) is a symbolic model that operates as a free nested structure of IF-THEN-ELSE and IF-ELSEIF-ELSE blocks:

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

where the [`antecedent`](@ref)s are formulas to be checked, and the [`consequent`](@ref)s are the feasible local outcomes of the block.

!!! note
    Note that `FM` refers to the Feasible Models (`FM`) allowed in the model's sub-tree.


See also [`AbstractModel`](@ref), [`Branch`](@ref)s, [`DecisionList`](@ref)s, [`DecisionTree`](@ref), [`Rule`](@ref)s.
