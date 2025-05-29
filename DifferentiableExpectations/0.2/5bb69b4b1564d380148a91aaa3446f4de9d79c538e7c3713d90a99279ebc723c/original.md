```
Reparametrization{threaded} <: DifferentiableExpectation{threaded}
```

Differentiable parametric expectation `F : θ -> 𝔼[f(X)]` where `X ∼ p(θ)` using the reparametrization (or pathwise) gradient estimator: if `X = g(Z,θ)` where `Z ∼ q` then

```
∂F(θ) = 𝔼_q[∂f(g(Z,θ)) ∂₂g(Z,θ)ᵀ]
```

# Example

```jldoctest
using DifferentiableExpectations, Distributions, Zygote

E = Reparametrization(exp, Normal; nb_samples=10^4)
E_true(μ, σ) = mean(LogNormal(μ, σ))

μ, σ = 0.5, 1,0
∇E, ∇E_true = gradient(E, μ, σ), gradient(E_true, μ, σ)
isapprox(collect(∇E), collect(∇E_true); rtol=1e-1)

# output

true
```

# Constructor

```
Reparametrization(
    f,
    dist_constructor,
    rng=Random.default_rng(),
    nb_samples=1,
    threaded=false,
    seed=nothing
)
```

# Fields

  * `f::Any`: function applied inside the expectation
  * `dist_constructor::Any`: constructor of the probability distribution `(θ...) -> p(θ)`
  * `rng::Random.AbstractRNG`: random number generator
  * `nb_samples::Int64`: number of Monte-Carlo samples
  * `seed::Union{Nothing, Int64}`: seed for the random number generator, reset before each call. Set to `nothing` for no seeding.

# See also

  * [`DifferentiableExpectation`](@ref)
