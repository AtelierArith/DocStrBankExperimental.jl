```
gcv_svd(Ψ::RegularizationProblem, b̄::AbstractVector, λ::AbstractFloat)
```

Compute the [Generalized Cross Validation](@ref) using the trace term using the SVD  algorithm. Requires that the vector b̄ is in standard form.

Example Usage

```julia
using Underscores

Ψ = setupRegularizationProblem(A, 1)            # Setup problem
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)              # Convert to standard form
Vλ = gcv_svd(Ψ, b̄, x̄₀, 0.1)                     # V(λ) single λ value
Vλ = @_ map(gcv_svd(Ψ, b̄, _), [0.1, 1.0, 10.0]) # V(λ) for array of λ
```
