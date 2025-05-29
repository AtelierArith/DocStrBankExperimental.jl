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

!!! compat
    This function is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref).


## Notes

  * For this method, you must explicitly set `autodiff = true`, because no user-provided gradient function `∇f` is given.
  * Second-derivative information is only computed if `dimension == 1`.
  * `op` does not have to be the same symbol as `f`, but it is generally more readable if it is.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f(x::T) where {T<:Real} = x^2
f (generic function with 1 method)

julia> register(model, :foo, 1, f; autodiff = true)

julia> @NLobjective(model, Min, foo(x))
```

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> g(x::T, y::T) where {T<:Real} = x * y
g (generic function with 1 method)

julia> register(model, :g, 2, g; autodiff = true)

julia> @NLobjective(model, Min, g(x[1], x[2]))
```
