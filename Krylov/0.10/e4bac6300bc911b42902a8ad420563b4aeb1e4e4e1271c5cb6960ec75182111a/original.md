```
workspace = krylov_workspace(method, args...; kwargs...)
workspace = krylov_workspace(Val(method), args...; kwargs...)
```

Generic function that dispatches to the appropriate workspace constructor for each subtype of [`KrylovWorkspace`](@ref) and [`BlockKrylovWorkspace`](@ref). In both calls, `method` is a symbol (such as `:cg`, `:gmres` or `:block_minres`) that specifies the (block) Krylov method for which a workspace is desired. The returned workspace can later be used by [`krylov_solve!`](@ref) to execute the (block) Krylov method in-place.

Pass the plain symbol `method` for convenience, or wrap it in `Val(method)` to enable full compile-time specialization, improve type inference, and achieve maximum performance.
