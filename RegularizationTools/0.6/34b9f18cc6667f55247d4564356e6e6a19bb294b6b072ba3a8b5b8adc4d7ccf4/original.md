```
Lcurve_functions(Ψ::RegularizationProblem, b̄::AbstractVector)
```

Compute the L-curve functions to evaluate the norms L1, L2, and the curvature κ.  Requires that the vectors b̄ is in standard form.

Example Usage

```julia
Ψ = setupRegularizationProblem(A, 1)
b̄ = to_standard_form(Ψ, b)
L1norm, L2norm, κ = Lcurve_functions(Ψ, b̄)

L1norm.([0.1, 1.0, 10.0])    # L1 norm for λ's
L2norm.([0.1, 1.0, 10.0])    # L2 norm for λ's
κ.([0.1, 1.0, 10.0])         # L-curve curvature for λ's
```
