```
check(
    φ::Formula,
    s::AbstractInterpretationSet,
    args...;
    kwargs...
)::Vector{Bool}
```

Check a formula on all instances of an [`AbstractInterpretationSet`](@ref).

See also [`AbstractInterpretationSet`](@ref), [`Formula`](@ref).
