```
register(
    model::Model,
    s::Symbol,
    dimension::Integer,
    f::Function,
    ∇f::Function,
    ∇²f::Function,
)
```

Register the user-defined function `f` that takes `dimension` arguments in `model` as the symbol `s`. In addition, provide a gradient function `∇f` and a hessian function `∇²f`.

`∇f` and `∇²f` must return numbers corresponding to the first- and second-order derivatives of the function `f` respectively.

## Notes

  * Because automatic differentiation is not used, you can assume the inputs are all `Float64`.
  * This method will throw an error if `dimension > 1`.
  * `s` does not have to be the same symbol as `f`, but it is generally more readable if it is.

## Examples

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
f(x::Float64) = x^2
∇f(x::Float64) = 2 * x
∇²f(x::Float64) = 2.0
register(model, :foo, 1, f, ∇f, ∇²f)
@NLobjective(model, Min, foo(x))
```
