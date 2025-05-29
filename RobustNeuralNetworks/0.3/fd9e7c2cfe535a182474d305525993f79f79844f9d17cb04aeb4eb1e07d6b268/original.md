```
LipschitzRENParams(nu, nx, nv, ny, γ; <keyword arguments>) where T
```

Construct direct parameterisation of a REN with a Lipschitz bound of γ.

# Arguments

  * `nu::Int`: Number of inputs.
  * `nx::Int`: Number of states.
  * `nv::Int`: Number of neurons.
  * `ny::Int`: Number of outputs.
  * `γ::Number`: Lipschitz upper bound.

# Keyword arguments

  * `nl::Function=relu`: Sector-bounded static nonlinearity.
  * `αbar::T=1`: Upper bound on the contraction rate with `ᾱ ∈ (0,1]`.
  * `learn_γ::Bool=false:` Whether to make the Lipschitz bound γ a learnable parameter.

See [`DirectRENParams`](@ref) for documentation of keyword arguments `init`, `ϵ`, `bx_scale`, `bv_scale`, `polar_param`, `D22_zero`, `rng`.

See also [`GeneralRENParams`](@ref), [`ContractingRENParams`](@ref), [`PassiveRENParams`](@ref).
