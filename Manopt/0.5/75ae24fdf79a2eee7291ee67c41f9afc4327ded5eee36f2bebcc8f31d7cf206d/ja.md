```
solve!(p::AbstractManoptProblem, s::AbstractManoptSolverState)
```

[`AbstractManoptProblem`](@ref)`p`と[`AbstractManoptSolverState`](@ref)`s`のために実装されたソルバーを実行し、[`initialize_solver!`](@ref)、[`step_solver!`](@ref)、およびソルバーの[`stop_solver!`](@ref)を使用します。
