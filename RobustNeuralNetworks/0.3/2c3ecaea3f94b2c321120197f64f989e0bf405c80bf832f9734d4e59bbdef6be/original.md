```
DenseLBDNParams{T}(nu, nh, ny, γ; <keyword arguments>) where T
```

Construct direct parameterisation of a dense (fully-connected) LBDN.

This is the equivalent of a multi-layer perceptron (eg: `Flux.Dense`) with a guaranteed Lipschitz bound of `γ`. Note that the Lipschitz bound can made a learnable parameter.

# Arguments

  * `nu::Int`: Number of inputs.
  * `nh::Union{Vector{Int}, NTuple{N, Int}}`: Number of hidden units for each layer. Eg: `nh = [5,10]` for 2 hidden layers with 5 and 10 nodes (respectively).
  * `ny::Int`: Number of outputs.
  * `γ::Real=T(1)`: Lipschitz upper bound, must be positive.

# Keyword arguments:

  * `nl::Function=relu`: Sector-bounded static nonlinearity.
  * `learn_γ::Bool=false:` Whether to make the Lipschitz bound γ a learnable parameter.

See [`DirectLBDNParams`](@ref) for documentation of keyword arguments `initW`, `initb`, `rng`.
