```
gcv_tr(
    Ψ::RegularizationProblem,
    b̄::AbstractVector,
    x̄₀::AbstractVector,
    λ::AbstractFloat,
)
```

Compute the [Generalized Cross Validation](@ref) using the trace term and intial guess.  Requires that the vectors b̄ and x̄₀ are in standard form.

$$
V(\lambda)=\frac{n\left\lVert {\bf {\rm {\bf \bar{A}}{\rm \bar{x}{}_{\lambda}}-
{\rm \bar{b}}}}\right\rVert _{2}^{2}}{tr({\rm {\bf I}-{\rm {\bar {\bf A}_{\lambda}})}^{2}}}
$$

Example Usage

```julia
using Underscores

Ψ = setupRegularizationProblem(A, 1)               # Setup problem
b̄, x̄₀ = to_standard_form(Ψ, b, x₀)                 # Convert to standard form
Vλ = gcv_tr(Ψ, b̄, x̄₀, 0.1)                         # V(λ) single λ value
Vλ = @_ map(gcv_tr(Ψ, b̄, x̄₀, _), [0.1, 1.0, 10.0]) # V(λ) for array of λ
```
