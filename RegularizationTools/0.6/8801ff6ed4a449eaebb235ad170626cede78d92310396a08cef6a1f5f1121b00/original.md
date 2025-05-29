```
solve(Ψ::RegularizationProblem, b̄::AbstractVector, x̄₀::AbstractVector, λ::AbstractFloat)
```

Compute the Tikhonov solution for problem Ψ in standard form for regularization parameter λ and using x̄₀ as initial guess. 

$$
{\rm x_{\lambda}}=\left({\rm {\bf \bar A}^{T}}{\rm {\bf \bar A}}+\lambda^{2}{\rm {\bf I}}\right)^{-1} 
\left({\rm {\bf {\bar A}}^{T}}{\rm {\bar b}} + \lambda^2 {\rm {\bar x}}_0 \right)
$$

Example Usage (Standard Syntax)

```julia
# A is a Matrix and b is a response vector. 
Ψ = setupRegularizationProblem(A, 2)     # Setup problem
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)       # Convert to standard form
x̄ = solve(A, b̄, x̄₀, 0.5)                 # Solve the equation
x = to_general_form(Ψ, b, x̄)             # Convert back to general form
```
