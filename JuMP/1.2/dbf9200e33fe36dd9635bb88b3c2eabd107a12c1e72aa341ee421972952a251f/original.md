```
register(
    model::Model,
    s::Symbol,
    dimension::Integer,
    f::Function,
    ∇f::Function;
    autodiff:Bool = false,
)
```

Register the user-defined function `f` that takes `dimension` arguments in `model` as the symbol `s`. In addition, provide a gradient function `∇f`.

The functions `f`and `∇f` must support all subtypes of `Real` as arguments. Do not assume that the inputs are `Float64`.

## Notes

  * If the function `f` is univariate (i.e., `dimension == 1`), `∇f` must return a number which represents the first-order derivative of the function `f`.
  * If the function `f` is multi-variate, `∇f` must have a signature matching `∇f(g::AbstractVector{T}, args::T...) where {T<:Real}`, where the first argument is a vector `g` that is modified in-place with the gradient.
  * If `autodiff = true` and `dimension == 1`, use automatic differentiation to compute the second-order derivative information. If `autodiff = false`, only first-order derivative information will be used.
  * `s` does not have to be the same symbol as `f`, but it is generally more readable if it is.

## Examples

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
f(x::T) where {T<:Real} = x^2
∇f(x::T) where {T<:Real} = 2 * x
register(model, :foo, 1, f, ∇f; autodiff = true)
@NLobjective(model, Min, foo(x))
```

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x[1:2])
g(x::T, y::T) where {T<:Real} = x * y
function ∇g(g::AbstractVector{T}, x::T, y::T) where {T<:Real}
    g[1] = y
    g[2] = x
    return
end
register(model, :g, 2, g, ∇g; autodiff = true)
@NLobjective(model, Min, g(x[1], x[2]))
```
