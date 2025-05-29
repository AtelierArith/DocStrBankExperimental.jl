```
function solve(
    Ψ::RegularizationProblem, 
    b::AbstractVector,
    lower::AbstractVector, 
    upper::AbstractVector;
    kwargs...
)
```

Constraint minimization of [RegularizationProblem](@ref) Ψ, with observations b and upper and lower bounds for each xᵢ.

The function computes the algebraic solution using `solve(Ψ, b; kwargs...)`, truncates the solution at the upper and lower bounds and uses this solution as initial condition for the minimization problem using a Least Squares numerical solver. The returned solution is using the regularization parameter λ obtained from the algebraic solution.
