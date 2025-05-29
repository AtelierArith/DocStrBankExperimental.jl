```
solver_startsolutions(args...; kwargs...)
```

[`solve`](@ref)と同じ入力を受け取りますが、問題を直接解くのではなく、[`Solver`](@ref)構造体と開始解を返します。

## 例

`solve(args..; kwargs...)`を呼び出すことは、次のように等価です。

```julia
solver, starts = solver_startsolutions(args...; kwargs...)
solve(solver, starts)
```
