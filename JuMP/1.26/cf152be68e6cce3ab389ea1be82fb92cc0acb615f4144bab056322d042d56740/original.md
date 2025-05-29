```
add_nonlinear_operator(
    model::Model,
    dim::Int,
    f::Function,
    [∇f::Function,]
    [∇²f::Function];
    [name::Symbol = Symbol(f),]
)
```

Add a new nonlinear operator with `dim` input arguments to `model` and associate it with the name `name`.

The function `f` evaluates the operator and must return a scalar.

The optional function `∇f` evaluates the first derivative, and the optional function `∇²f` evaluates the second derivative.

`∇²f` may be provided only if `∇f` is also provided.

## Univariate syntax

If `dim == 1`, then the method signatures of each function must be:

  * `f(::T)::T where {T<:Real}`
  * `∇f(::T)::T where {T<:Real}`
  * `∇²f(::T)::T where {T<:Real}`

## Multivariate syntax

If `dim > 1`, then the method signatures of each function must be:

  * `f(x::T...)::T where {T<:Real}`
  * `∇f(g::AbstractVector{T}, x::T...)::Nothing where {T<:Real}`
  * `∇²f(H::AbstractMatrix{T}, x::T...)::Nothing where {T<:Real}`

Where the gradient vector `g` and Hessian matrix `H` are filled in-place. For the Hessian, you must fill in the non-zero lower-triangular entries only. Setting an off-diagonal upper-triangular element may error.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f(x::Float64) = x^2
f (generic function with 1 method)

julia> ∇f(x::Float64) = 2 * x
∇f (generic function with 1 method)

julia> ∇²f(x::Float64) = 2.0
∇²f (generic function with 1 method)

julia> op_f = add_nonlinear_operator(model, 1, f, ∇f, ∇²f)
NonlinearOperator(f, :f)

julia> @objective(model, Min, op_f(x))
f(x)

julia> op_f(2.0)
4.0
```
