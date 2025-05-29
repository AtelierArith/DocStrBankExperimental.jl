```
DirectLBDNParams{T}(nu, nh, ny, γ; <keyword arguments>) where T
```

Construct direct parameterisation for a Lipschitz-bounded deep network.

This is typically used by a higher-level constructor to define an LBDN model, which takes the direct parameterisation in `DirectLBDNParams` and defines rules for converting it to an explicit parameterisation. See for example [`DenseLBDNParams`](@ref).

# Arguments

  * `nu::Int`: Number of inputs.
  * `nh::Union{Vector{Int}, NTuple{N, Int}}`: Number of hidden units for each layer. Eg: `nh = [5,10]` for 2 hidden layers with 5 and 10 nodes (respectively).
  * `ny::Int`: Number of outputs.
  * `γ::Real=T(1)`: Lipschitz upper bound, must be positive.

# Keyword arguments

  * `initW::Function=Flux.glorot_normal`: Initialisation function for implicit params `X,Y,d`.
  * `initb::Function=Flux.glorot_normal`: Initialisation function for bias vectors.
  * `learn_γ::Bool=false:` Whether to make the Lipschitz bound γ a learnable parameter.
  * `rng::AbstractRNG = Random.GLOBAL_RNG`: rng for model initialisation.

See [Wang et al. (2023)](https://proceedings.mlr.press/v202/wang23v.html) for parameterisation details.

See also [`DenseLBDNParams`](@ref).
