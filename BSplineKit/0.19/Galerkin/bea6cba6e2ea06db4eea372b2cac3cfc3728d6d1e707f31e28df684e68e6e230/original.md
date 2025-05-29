```
galerkin_projection!(
    f, φ::AbstractVector, B::AbstractBSplineBasis, [deriv = Derivative(0)],
)
```

Compute Galerkin projection $φ_i = ⟨ b_i, f ⟩$.

See [`galerkin_projection`](@ref) for details.
