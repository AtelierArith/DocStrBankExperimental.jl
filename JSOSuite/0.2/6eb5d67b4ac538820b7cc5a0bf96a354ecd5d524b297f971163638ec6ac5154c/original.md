```
stats = feasible_point(nlp::Union{AbstractNLPModel, JuMP.Model}; kwargs...)
stats = feasible_point(nlp::Union{AbstractNLPModel, JuMP.Model}, solver_name::Symbol; kwargs...)
```

Compute a feasible point of the optimization problem `nlp`. The signature is the same as the function [`minimize`](@ref).

## Output

The value returned is a `GenericExecutionStats`, see `SolverCore.jl`, where the `status`, `solution`, `primal_residual`, `iter` and `time` are filled-in.

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
