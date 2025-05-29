```julia
mutable struct MCCallback{FH, FJ, C<:McCormick.AbstractContractorMC, PRE<:McCormick.AbstractPreconditionerMC, N, T<:McCormick.RelaxTag, AMAT<:(AbstractMatrix)} <: McCormick.AbstractMCCallback
```

A structure used to compute implicit relaxations.

  * `h!::Any`: Function h(x,p) = 0 defined in place by h!(out,x,p)
  * `hj!::Any`: Jacobian of h(x,p) w.r.t x
  * `H::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: Intermediate inplace storage for output of h!
  * `J::AbstractMatrix`: Intermediate inplace storage for output of hj!
  * `J0::Vector{AMAT} where AMAT<:(AbstractMatrix)`
  * `xz0::Vector{AMAT} where AMAT<:(AbstractMatrix)`
  * `xmid::Vector{Float64}`
  * `X::Vector{IntervalArithmetic.Interval{Float64}}`: State space `x` interval bounds
  * `P::Vector{IntervalArithmetic.Interval{Float64}}`: Decision space `p` interval bounds
  * `nx::Int64`: State space dimension
  * `np::Int64`: Decision space dimension
  * `λ::Float64`: Convex combination parameter
  * `eps::Float64`: Tolerance for interval equality
  * `kmax::Int64`: Number of contractor steps to take
  * `pref_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: Reference decision point at which affine relaxations are calculated (and used in subsequent calculations).
  * `p_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: Decision point at which relaxation is evaluated.
  * `p_temp_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: Vector used to temporarily store p in gen*expansion*params! routine.
  * `x0_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `x_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `xa_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `xA_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `aff_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `z_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `contractor::McCormick.AbstractContractorMC`: Type of contractor used in implicit relaxation routine.
  * `preconditioner::McCormick.AbstractPreconditionerMC`: Preconditioner used in the implicit relaxation routine.
  * `apply_precond::Bool`: Boolean indicating that the preconditioner should be applied
  * `param::Array{Array{McCormick.MC{N, T}, 1}, 1} where {N, T<:McCormick.RelaxTag}`: Vector of relaxations of `x` at each iteration used to generated affine relaxations used in intermediate calculation.
  * `use_apriori::Bool`: Indicates that subgradient-based apriori relaxations of multiplication should be used.
