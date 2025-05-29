```
check(
    φ::Formula,
    s::AbstractInterpretationSet,
    i_instance::Integer,
    args...;
    kwargs...
)::Bool
```

Check a formula on the $i$-th instance of an [`AbstractInterpretationSet`](@ref).

See also [`AbstractInterpretationSet`](@ref), [`Formula`](@ref).
