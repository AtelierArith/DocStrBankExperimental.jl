```
PassiveRENParams{T}(nu, nx, nv, ny, ν, ρ; <keyword arguments>) where T
```

Construct direct parameterisation of a passive REN.

# Arguments

  * `nu::Int`: Number of inputs.
  * `nx::Int`: Number of states.
  * `nv::Int`: Number of neurons.
  * `ny::Int`: Number of outputs.
  * `ν::Number=0`: Passivity index. Use `ν > 0` for an incrementally strictly input passive model. Set both `ν = 0` and `ρ = 0` for incrementally passive model.
  * `ρ::Number=0`: Passivity index. Use `ρ > 0` for an incrementally strictly output passive model.

Note that the product of passivity indices ρν has to be less than 1/4 for passive REN.

# Keyword arguments

  * `nl::Function=relu`: Sector-bounded static nonlinearity.
  * `αbar::T=1`: Upper bound on the contraction rate with `ᾱ ∈ (0,1]`.

See [`DirectRENParams`](@ref) for documentation of keyword arguments `init`, `ϵ`, `bx_scale`, `bv_scale`, `polar_param`, `rng`.

See also [`GeneralRENParams`](@ref), [`ContractingRENParams`](@ref), [`LipschitzRENParams`](@ref).
