```julia
struct PEPSOptimize{G}
```

Algorithm struct for PEPS ground-state optimization using AD. See [`fixedpoint`](@ref) for details.

## Fields

  * `boundary_alg::PEPSKit.CTMRGAlgorithm`
  * `gradient_alg::Any`
  * `optimizer_alg::OptimKit.OptimizationAlgorithm`
  * `reuse_env::Bool`
  * `symmetrization::Union{Nothing, PEPSKit.SymmetrizationStyle}`

## Constructors

```
PEPSOptimize(; kwargs...)
```

Construct a PEPS optimization algorithm struct based on keyword arguments. For a full description, see [`fixedpoint`](@ref). The supported keywords are:

  * `boundary_alg::Union{NamedTuple,<:CTMRGAlgorithm}`
  * `gradient_alg::Union{NamedTuple,Nothing,<:GradMode}`
  * `optimizer_alg::Union{NamedTuple,<:OptimKit.OptimizationAlgorithm}`
  * `reuse_env::Bool=true`
  * `symmetrization::Union{Nothing,SymmetrizationStyle}=nothing`
