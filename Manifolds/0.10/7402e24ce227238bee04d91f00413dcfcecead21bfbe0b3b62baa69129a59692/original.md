```
rand(::ProbabilitySimplex; vector_at=nothing, σ::Real=1.0)
```

When `vector_at` is `nothing`, return a random (uniform over the Fisher-Rao metric; that is, uniform with respect to the `n`-sphere whose positive orthant is mapped to the simplex). point `x` on the [`ProbabilitySimplex`](@ref) manifold `M` according to the isometric embedding into the `n`-sphere by normalizing the vector length of a sample from a multivariate Gaussian. See [Marsaglia:1972](@cite).

When `vector_at` is not `nothing`, return a (Gaussian) random vector from the tangent space $T_{p}\mathrm{\Delta}^n$by shifting a multivariate Gaussian with standard deviation `σ` to have a zero component sum.
