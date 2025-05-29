```
register(
    model::Model,
    op::Symbol,
    dimension::Integer,
    f::Function;
    autodiff:Bool = false,
)
```

Register the user-defined function `f` that takes `dimension` arguments in `model` as the symbol `op`.

The function `f` must support all subtypes of `Real` as arguments. Do not assume that the inputs are `Float64`.

## Notes

  * For this method, you must explicitly set `autodiff = true`, because no user-provided gradient function `∇f` is given.
  * Second-derivative information is only computed if `dimension == 1`.
  * `op` does not have to be the same symbol as `f`, but it is generally more readable if it is.

## Examples

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
f(x::T) where {T<:Real} = x^2
register(model, :foo, 1, f; autodiff = true)
@NLobjective(model, Min, foo(x))
```

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x[1:2])
g(x::T, y::T) where {T<:Real} = x * y
register(model, :g, 2, g; autodiff = true)
@NLobjective(model, Min, g(x[1], x[2]))
```
