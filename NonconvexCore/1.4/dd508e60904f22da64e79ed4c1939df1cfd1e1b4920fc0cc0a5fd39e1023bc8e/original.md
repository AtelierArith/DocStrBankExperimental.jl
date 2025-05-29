```
struct Model <: AbstractModel
    objective::Objective
    eq_constraints::VectorOfFunctions
    ineq_constraints::VectorOfFunctions
    box_min::AbstractVector
    box_max::AbstractVector
    init::AbstractVector
    integer::AbstractVector
end
```

The `Model` structs stores information about the nonlinear optimization problem.

  * `objective`: the objective function of the problem of type [`Objective`](@ref).
  * `eq_constraints`: the equality constraints of the problem of type [`VectorOfFunctions`](@ref). Each function in `ineq_constraints` can be an instance of [`IneqConstraint`](@ref) or [`AbstractFunction`](@ref). If the function is not an `IneqConstraint`, its right-hand-side bound is assumed to be 0.
  * `ineq_constraints`: the inequality constraints of the problem of type [`VectorOfFunctions`](@ref). Each function in `ineq_constraints` can be an instance of [`IneqConstraint`](@ref) or [`AbstractFunction`](@ref). If the function is not an `IneqConstraint`, its right-hand-side bound is assumed to be 0.
  * `sd_constraints`: a list of matrix-valued functions which must be positive semidefinite at any feasible solution.
