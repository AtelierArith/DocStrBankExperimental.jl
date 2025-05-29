```
ContractingRENParams{T}(nu, nx, nv, ny; <keyword arguments>) where T
```

Construct direct parameterisation of a contracting REN.

The parameters can be used to construct an explicit [`REN`](@ref) model that has guaranteed, built-in contraction properties.

# Arguments

  * `nu::Int`: Number of inputs.
  * `nx::Int`: Number of states.
  * `nv::Int`: Number of neurons.
  * `ny::Int`: Number of outputs.

# Keyword arguments

  * `nl::Function=relu`: Sector-bounded static nonlinearity.
  * `αbar::T=1`: Upper bound on the contraction rate with `ᾱ ∈ (0,1]`.

See [`DirectRENParams`](@ref) for documentation of keyword arguments `init`, `ϵ`, `bx_scale`, `bv_scale`, `polar_param`, `D22_zero`, `output_map`, `rng`.

See also [`GeneralRENParams`](@ref), [`LipschitzRENParams`](@ref), [`PassiveRENParams`](@ref).
