```
GeneralRENParams{T}(nu, nx, nv, ny, Q, S, R; <keyword arguments>) where T
```

Construct direct parameterisation of a REN satisfying general behavioural constraints.

Behavioural constraints are encoded by the matrices `Q,S,R` in an incremental Integral Quadratic Constraint (IQC). See Equation 4 of [Revay et al. (2021)](https://arxiv.org/abs/2104.05942).

# Arguments

  * `nu::Int`: Number of inputs.
  * `nx::Int`: Number of states.
  * `nv::Int`: Number of neurons.
  * `ny::Int`: Number of outputs.
  * `Q::AbstractMatrix`: IQC weight matrix on model outputs
  * `S::AbstractMatrix`: IQC coupling matrix on model outputs/inputs
  * `R::AbstractMatrix`: IQC weight matrix on model outputs

# Keyword arguments

  * `nl::Function=relu`: Sector-bounded static nonlinearity.
  * `αbar::T=1`: Upper bound on the contraction rate with `ᾱ ∈ (0,1]`.

See [`DirectRENParams`](@ref) for documentation of keyword arguments `init`, `ϵ`, `bx_scale`, `bv_scale`, `polar_param`, `rng`.

See also [`ContractingRENParams`](@ref), [`LipschitzRENParams`](@ref), [`PassiveRENParams`](@ref).
