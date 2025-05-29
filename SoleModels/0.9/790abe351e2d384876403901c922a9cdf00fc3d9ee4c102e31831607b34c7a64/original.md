```
checkantecedent(
    m::Union{Rule,Branch},
    args...;
    kwargs...
)
    check(antecedent(m), args...; kwargs...)
end
```

Check the [`antecedent`](@ref) of a [`Rule`](@ref) or a [`Branch`](@ref), on an instance or dataset.

See also [`antecedent`](@ref), [`Rule`](@ref), [`Branch`](@ref).
