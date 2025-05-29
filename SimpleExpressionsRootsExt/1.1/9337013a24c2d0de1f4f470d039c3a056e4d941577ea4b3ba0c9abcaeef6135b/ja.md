```
solve(ex::SymbolicEquation, x, args...; kwargs...)
solve(ex::SymbolicEquation, a::Real, b::Real; kwargs...)
```

最初のケースは `find_zero` を使用し、2番目は `find_zeros` を使用します。
