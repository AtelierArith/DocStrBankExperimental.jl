```
FletcherPenaltyNLP(nlp, σ, hessian_approx, [x0 = nlp.meta.x0]; qds = LDLtSolver(nlp, S(0)))
FletcherPenaltyNLP(nlp, σ, ρ, δ, hessian_approx, [x0 = nlp.meta.x0]; qds = LDLtSolver(nlp, S(0)))
FletcherPenaltyNLP(nlp; σ_0 = 1, ρ_0 = 0, δ_0 = 0, hessian_approx = Val(2), x0 = nlp.meta.x0, qds = LDLtSolver(nlp, S(0)))
```

We consider here the implementation of Fletcher's exact penalty method for the minimization problem:

$$
    minₓ    f(x)    s.t.    c(x) = ℓ, l ≤ x ≤ u
$$

using Fletcher penalty function:

$$
    minₓ    f(x) - (c(x) - ℓ)^T ys(x) + 0.5 ρ ||c(x) - ℓ||²₂    s.t.    l ≤ x ≤ u
$$

where

$$
    ys(x)    ∈    arg min\_y    0.5 ||A(x)y - g(x)||²₂ + σ (c(x) - ℓ)^T y + 0.5 || δ ||²₂
$$

# Arguments

  * `nlp::AbstractNLPModel`: the model solved, see `NLPModels.jl`;
  * `x::S`: Initial guess. If `x` is not specified, then `nlp.meta.x0` is used;
  * `σ`, `ρ`, `δ` parameters of the subproblem;
  * `hessian_approx` either `Val(1)` or `Val(2)` for the hessian approximation.
  * `qds`: solver structure for the linear algebra computations, see [`LDLtSolver`](@ref) or [`IterativeSolver`](@ref).

# Notes:

  * Evaluation of the `obj`, `grad`, `objgrad` functions evaluate functions from the orginial `nlp`. These values are stored in `fx`, `cx`, `gx`.
  * The value of the penalty vector `ys` is also stored.
  * The hessian's structure is dense.

# Examples

```julia
julia> using FletcherPenaltySolver, ADNLPModels
julia> nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0])
julia> fp_sos  = FletcherPenaltyNLP(nlp)
```
