```
checkantecedent(
    m::Union{Rule,Branch},
    args...;
    kwargs...
)
    check(antecedent(m), args...; kwargs...)
end
```

Simply check the antecedent of a rule on an instance or dataset.

See also [`antecedent`](@ref), [`Rule`](@ref), [`Branch`](@ref).
