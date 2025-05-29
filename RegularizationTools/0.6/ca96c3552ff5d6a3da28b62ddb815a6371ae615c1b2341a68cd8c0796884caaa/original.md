```
gcv_tr(Ψ::RegularizationProblem, b̄::AbstractVector, λ::AbstractFloat)
```

Compute the [Generalized Cross Validation](@ref) using the trace term. Requires that the  vector b̄ is in standard form.

$$
V(\lambda)=\frac{n\left\lVert ({\bf {\rm {\bf {\bf I}-}{\bf \bar {A}_{\lambda}})
{\bar{\rm b}}}}\right\rVert _{2}^{2}}{tr({\rm {\bf I}-{\rm {\bar {\bf A}_{\lambda}})}^{2}}}
$$

Example Usage

```julia
using Underscores

Ψ = setupRegularizationProblem(A, 1)           # Setup problem
b̄ = to_standard_form(Ψ, b)                     # Convert to standard form
Vλ = gcv_tr(Ψ, b̄, 0.1)                         # V(λ) single λ value
Vλ = @_ map(gcv_tr(Ψ, b̄, _), [0.1, 1.0, 10.0]) # V(λ) for array of λ
```
