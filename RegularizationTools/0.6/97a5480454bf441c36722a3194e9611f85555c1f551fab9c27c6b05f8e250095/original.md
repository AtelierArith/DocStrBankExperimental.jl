```
function solve(
    Ψ::RegularizationProblem,
    b::AbstractVector;
    alg = :gcv_svd,
    method = Brent(),
    λ₁ = 0.0001,
    λ₂ = 1000.0,
    λ₀ = 1.0,
    kwargs...
)
```

Find the optimum regularization parameter λ using the algorithm `alg` and optimization `method`. Choices for algorithms are

```
    :gcv_tr - generalized cross validation using the trace formulation (slow)
    :gcv_svd - generalized cross validation using the SVD decomposition (fast)
    :L_curve - L-curve algorithm 
```

Optimization methods are those available in the Optim package. Methods that optimize on bounds (`Brent()` and `GoldenSection()`) will use [λ₁, λ₂] for bounds. Other methods will use λ₀ for the initial guess. The methods `Brent()` (default) and `NelderMead()` are recommended. Any additional keyword arguments will be passed on to the optimization method.

!!! tip
    The gcv_svd algorithm is fastest and most stable. The L_curve algorithn is sensitive to the upper  and lower bound. Specify narrow upper and lower bounds to obtain a good solution.


The solve function takes the original data, converts it to standard form, performs the search within the specified bounds and returns a [RegularizatedSolution](@ref)

Example Usage (Standard Syntax)

```julia
# A is a Matrix and b is a response vector. 
Ψ = setupRegularizationProblem(A, 2)     # Setup problem
sol = solve(Ψ, b)                        # Solve it
```

Example Usage (Lazy Syntax)

```julia
# A is a Matrix and b is a response vector. 
sol = @> setupRegularizationProblem(A, 1) solve(b)
```
