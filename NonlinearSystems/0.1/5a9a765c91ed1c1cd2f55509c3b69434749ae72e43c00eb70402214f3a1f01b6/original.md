```
NonlinearSystem(::Type{P}, fdf::OnceDifferentiable, x, fx, dx, solver; kwargs...)
```

Construct a `NonlinearSystem` for holding all information used for solving a nonlinear system of equations with problem type `P`. Users are not expected to use this method directly but should instead call `init` or `solve` to generate the problem. Any keyword argument passed to `init` or `solve` that is not accepted by a specific solution algorithm is passed to the constructor of `NonlinearSystem`. For the relevant solution algorithms, see [`Hybrid`](@ref).

# Keywords

  * `lower::Union{AbstractVector, Nothing}=nothing`: element-wise lower bounds for solution candidates.
  * `upper::Union{AbstractVector, Nothing}=nothing`: element-wise upper bounds for solution candidates.
  * `maxiter::Integer=1000`: maximum number of iteration allowed before terminating.
  * `ftol::Real=1e-8`: absolute tolerance for the infinity norm of residuals `fx`.
  * `gtol::Real=1e-10`: absolute tolerance for the infinity norm of gradient vector; only relevant for solving least squares.
  * `xtol::Real=0.0`: absolute tolerance for the infinity norm of a step `dx`.
  * `xtolr::Real=0.0`: relative tolerance for the infinity norm of a step `dx` as a proportion of `x`.
  * `showtrace::Union{Bool,Integer}=false`: print summary information for each trial made by the solver; with `showtrace=true`, information is printed once every 20 iterations; an interger value specifies the gap for printing.
