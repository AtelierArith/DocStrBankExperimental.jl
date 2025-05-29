```
lmsolve(
    fun,
    jac,
    x0::StaticVector{N, <:AbstractFloat},
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...
) -> x, F, info, iter, nfev, njev

lmsolve!(
    fun!,
    jac!,
    x0::AbstractVector{<:AbstractFloat},
    m::Integer = length(x0),
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...,
) -> x, F, info, iter, nfev, njev, LM, solver

lmsolve!(
    fun!,
    jac!,
    x0::AbstractVector{<:AbstractFloat},
    f::AbstractVector{<:AbstractFloat},
    J::AbstractMatrix{<:AbstractFloat},
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...,
) -> x, F, info, iter, nfev, njev, LM, solver

lmsolve!(
    fun!,
    jac!,
    LM::LMWorkspace,
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...
) -> x, F, info, iter, nfev, njev, LM, solver
```

Minimize `F(x) = ||f(x)||^2` using the Levenberg-Marquardt algorithm.

### Arguments

  * `fun/fun!`: function to be minimized `||f||^2`, `f = fun(x, data)`,   `f = fun!(f, x, data)`
  * `jac/jac!`: jacobian of `f`, `J = jac(x, data)`, `J = jac!(J, x, data)`
  * `x0::AbstractVector{<:AbstractFloat}`: initial guess
  * `m::Integer = length(x0)`: number of function values
  * `data = nothing`: data passed to `fun/fun!` and `jac/jac!`
  * `f::AbstractVector{<:AbstractFloat}`: preallocated function vector
  * `J::AbstractMatrix{<:AbstractFloat}`: preallocated Jacobian matrix
  * `LM::LMWorkspace`: preallocated workspace
  * `lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing`: lower bounds   for `x`. Vectors must have same length as `x`
  * `ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing`: upper bounds   for `x`. Vectors must have same length as `x`

### Keywords

  * `solver::Union{Nothing, Symbol} = nothing`: linear solver for `lmsolve!`       (`lmsolve` always uses Cholesky factorization)

      * `nothing`: QR for dense Jacobian, Cholesky for sparse Jacobian
      * `:cholesky`: Cholesky factorization
      * `:qr`: QR factorization
  * `ftol::Real = eps(eltype(x))`: relative tolerance for function:   both actual and predicted reductions are less than `ftol`
  * `xtol::Real = 1e-10`: relative tolerance for change in `x`:   `all(abs(x - xk) < xtol * (xtol + abs(x)))`
  * `gtol::Real = eps(eltype(x))`: tolerance for gradient:   `norm(g, Inf) < gtol`
  * `maxit::Integer = 1000`: maximum number of iterations
  * `factor::Real = 1e-6`: initial factor for damping
  * `factoraccept::Real = 13`: factor for decreasing damping on good step
  * `factorreject::Real = 3`: factor for increasing damping on bad step
  * `factorupdate::Symbol = :marquardt`: factor update method   `∈ (:marquardt, :nielsen)`
  * `minscale::Real = 1e-12`: diagonal scaling lower bound
  * `maxscale::Real = 1e16`: diagonal scaling upper bound
  * `minfactor::Real = 1e-28`: damping factor lower bound
  * `maxfactor::Real = 1e32`: damping factor upper bound

### Returns

  * `x/LM.x`: solution
  * `F`: final objective
  * `info::Int`: convergence status

      * `1`: both actual and predicted reductions are less than `ftol`
      * `2`: relative difference between two consecutive iterates is less than `xtol`
      * `3`: inf norm of the gradient is less than `gtol`
      * `-1`: `maxit` reached
  * `iter::Int`: number of iterations
  * `nfev::Int`: number of function evaluations
  * `njev::Int`: number of Jacobian evaluations
  * `LM::LMWorkspace`: workspace
  * `solver::AbstractSolver`: solver

### Notes

In the returned `LMWorkspace`, only `LM.x` and `LM.f` are guaranteed to be updated. That is, `LM.J` might not be the Jacobian at the returned `x`.
