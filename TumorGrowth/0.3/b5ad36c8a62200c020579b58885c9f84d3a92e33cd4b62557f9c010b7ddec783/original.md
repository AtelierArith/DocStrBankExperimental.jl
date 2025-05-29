```
bertalanffy2(times, p; capacity=false, solve_kwargs...)
```

Return volumes for specified `times`, based on numerical solutions to a two-dimensional extension of General Bertalanffy model for lesion growth. Here `p` will have properties `v0`, `v∞`, `ω`, `λ`, `γ`, where `v0` is the volume at time `times[1]`.

The usual General Bertalanffy model is recovered when `γ=0`. In that case, using [`bertalanffy`](@ref), which is based on an analytic solution, may be preferred. Other parameters are explained below.

# Keyword options

  * `solve_kwargs`: optional keyword arguments for the ODE solver, `DifferentialEquations.solve`, from DifferentialEquations.jl.

# Underlying ODE

In this model the carrying capacity of the [`bertalanffy`](@ref) model, ordinarily fixed, is introduced as a new latent variable $u(t)$, which is allowed to evolve independently of the volume $v(t)$, at a rate in proportion to its magnitude:

$dv/dt = ω B_λ(u/v) v$

$du/dt = γωu$

Here $B_λ$ is the Box-Cox transformation with exponent $λ$. See [`bertalanffy`](@ref). Also:

  * $1/ω$ has units of time
  * $λ$ is dimensionless
  * $γ$ is dimensionless

Since $u$ is a latent variable, its initial value, `v∞ ≡ u(times[1])`, is an additional model parameter.

For a list of all models see [`TumorGrowth`](@ref). 
