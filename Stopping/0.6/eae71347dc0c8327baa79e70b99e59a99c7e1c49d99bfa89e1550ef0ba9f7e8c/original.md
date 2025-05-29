Type: NLPAtX

Methods: update!, reinit!

NLPAtX contains the information concerning a nonlinear optimization model at the iterate x.

min_{x ∈ ℜⁿ} f(x) subject to lcon <= c(x) <= ucon, lvar <= x <= uvar.

Tracked data include:

  * x             : the current iterate
  * fx [opt]      : function evaluation at x
  * gx [opt]      : gradient evaluation at x
  * Hx [opt]      : hessian evaluation at x
  * mu [opt]      : Lagrange multiplier of the bounds constraints
  * cx [opt]      : evaluation of the constraint function at x
  * Jx [opt]      : jacobian matrix of the constraint function at x
  * lambda        : Lagrange multiplier of the constraints
  * d [opt]       : search direction
  * res [opt]     : residual
  * current_time  : time
  * current_score : score

(import the type NLPModels.Counters)

Constructors:  `NLPAtX(:: T, :: T, :: S; fx :: eltype(T) = _init_field(eltype(T)), gx :: T = _init_field(T), Hx :: Matrix{eltype(T)} = _init_field(Matrix{eltype(T)}), mu :: T = _init_field(T), cx :: T = _init_field(T), Jx :: SparseMatrixCSC{eltype(T), Int64} = _init_field(SparseMatrixCSC{eltype(T), Int64}), d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64 = NaN) where {S, T <: AbstractVector}`

`NLPAtX(:: T; fx :: eltype(T) = _init_field(eltype(T)), gx :: T = _init_field(T), Hx :: Matrix{eltype(T)} = _init_field(Matrix{eltype(T)}), mu :: T = _init_field(T), current_time :: Float64 = NaN, current_score :: Union{T,eltype(T)} = _init_field(eltype(T))) where {T <: AbstractVector}`

`NLPAtX(:: T, :: T; fx :: eltype(T) = _init_field(eltype(T)), gx :: T = _init_field(T), Hx :: Matrix{eltype(T)} = _init_field(Matrix{eltype(T)}), mu :: T = _init_field(T), cx :: T = _init_field(T), Jx :: SparseMatrixCSC{eltype(T), Int64} = _init_field(SparseMatrixCSC{eltype(T), Int64}), d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64  = NaN, current_score :: Union{T,eltype(T)} = _init_field(eltype(T))) where T <: AbstractVector`

Note:

  * By default, unknown entries are set using `_init_field`.
  * By default the type of `current_score` is `eltype(x)` and cannot be changed once the State is created.    To have a vectorized `current_score` of length n, try something like `GenericState(x, Array{eltype(x),1}(undef, n))`.
  * All these information (except for `x` and `lambda`) are optionnal and need to be update when  required. The update is done through the `update!` function.
  * `x` and `lambda` are mandatory entries. If no constraints `lambda = []`.
  * The constructor check the size of the entries.

See also: `GenericState`, `update!`, `update_and_start!`, `update_and_stop!`, `reinit!`
