```
defaultconsequent(m::DecisionList)
```

Return the default [`consequent`](@ref) of `m`.

!!! note
    The returned model is complete if and only if `m` is complete. See also [`iscomplete`](@ref).


See also [`AbstractModel`](@ref), [`DecisionList`](@ref), [`Rule`](@ref).
