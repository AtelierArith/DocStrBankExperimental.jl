```
solve(Ψ::RegularizationProblem, b̄::AbstractVector, λ::AbstractFloat)
```

Compute the Tikhonov solution for problem Ψ in standard form for regularization parameter λ and using zero as initial guess. Returns a vector $\rm {\bar x}_\lambda$. 

$$
{\rm x_{\lambda}}=\left({\rm {\bf \bar A}^{T}}{\rm {\bf \bar A}}+\lambda^{2}{\rm {\bf I}}\right)^{-1} 
{\rm {\bf {\bar A}}^{T}}{\rm {\bar b}} 
$$

Example Usage (Standard Syntax)

```julia
# A is a Matrix and b is a response vector. 
Ψ = setupRegularizationProblem(A, 1)     # Setup problem
b̄ = to_standard_form(Ψ, b)               # Convert to standard form
x̄ = solve(A, b̄, 0.5)                     # Solve the equation
x = to_general_form(Ψ, b, x̄)             # Convert back to general form
```

Example Usage (Lazy Syntax)

```julia
# A is a Matrix and b is a response vector. 
Ψ = setupRegularizationProblem(A, 1)     # Setup problem
b̄ = @>> b to_standard_form(Ψ)            # Convert to standard form
x̄ = solve(A, b̄, 0.5)                     # Solve the equation
x = @>> x̄ to_general_form(Ψ, b)          # Convert back to general form
```
