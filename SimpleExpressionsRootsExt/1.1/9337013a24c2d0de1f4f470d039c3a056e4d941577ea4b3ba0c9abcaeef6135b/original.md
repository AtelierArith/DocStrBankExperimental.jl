```
solve(ex::SymbolicEquation, x, args...; kwargs...)
solve(ex::SymbolicEquation, a::Real, b::Real; kwargs...)
```

The first case uses `find_zero`, the second `find_zeros`.
