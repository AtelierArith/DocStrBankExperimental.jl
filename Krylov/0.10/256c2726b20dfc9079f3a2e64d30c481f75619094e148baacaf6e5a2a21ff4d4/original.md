```
krylov_solve(method, args...; kwargs...)
krylov_solve(Val(method), args...; kwargs...)
```

Generic function that dispatches to the appropriate out-of-place (block) Krylov method specified by `method`. In both calls, `method` is a symbol (such as `:cg`, `:gmres` or `:block_minres`).

Pass the plain symbol `method` for convenience, or wrap it in `Val(method)` to enable full compile-time specialization, improve type inference, and achieve maximum performance.
