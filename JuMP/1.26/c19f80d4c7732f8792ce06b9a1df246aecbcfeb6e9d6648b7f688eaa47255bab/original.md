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

!!! compat
    This function is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref).


## Notes

  * Because automatic differentiation is not used, you can assume the inputs are all `Float64`.
  * This method will throw an error if `dimension > 1`.
  * `s` does not have to be the same symbol as `f`, but it is generally more readable if it is.

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

julia> register(model, :foo, 1, f, ∇f, ∇²f)

julia> @NLobjective(model, Min, foo(x))

```
