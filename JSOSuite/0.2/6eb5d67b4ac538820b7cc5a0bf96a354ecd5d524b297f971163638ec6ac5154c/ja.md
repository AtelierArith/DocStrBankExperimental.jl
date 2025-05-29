```
stats = feasible_point(nlp::Union{AbstractNLPModel, JuMP.Model}; kwargs...)
stats = feasible_point(nlp::Union{AbstractNLPModel, JuMP.Model}, solver_name::Symbol; kwargs...)
```

最適化問題 `nlp` の実行可能な点を計算します。シグネチャは関数 [`minimize`](@ref) と同じです。

## 出力

返される値は `GenericExecutionStats` であり、`SolverCore.jl` を参照してください。ここでは `status`、`solution`、`primal_residual`、`iter`、および `time` が埋め込まれます。

```jldoctest; output = false
using ADNLPModels, JSOSuite
c(x) = [10 * (x[2] - x[1]^2); x[1] - 1]
b = zeros(2)
nlp = ADNLPModel(x -> 0.0, [-1.2; 1.0], c, b, b)
stats = feasible_point(nlp, verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```
