```
coefficients(f::Expression, vars::AbstractVector{Variable}; expanded = false)
```

Return all coefficients of the given polynomial `f` for the given variables `vars`. If `expanded = true` then this assumes that the expression `f` is already expanded, e.g., with [`expand`](@ref).
