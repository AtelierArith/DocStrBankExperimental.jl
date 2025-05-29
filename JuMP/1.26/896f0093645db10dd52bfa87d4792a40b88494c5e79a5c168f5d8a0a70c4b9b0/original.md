```
NonlinearOperator(func::Function, head::Symbol)
```

A callable struct (functor) representing a function named `head`.

When called with [`AbstractJuMPScalar`](@ref)s, the struct returns a [`GenericNonlinearExpr`](@ref).

When called with non-JuMP types, the struct returns the evaluation of `func(args...)`.

Unless `head` is special-cased by the optimizer, the operator must have already been added to the model using [`add_nonlinear_operator`](@ref) or [`@operator`](@ref).

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

julia> @operator(model, op_f, 1, f, ∇f, ∇²f)
NonlinearOperator(f, :op_f)

julia> bar = NonlinearOperator(f, :op_f)
NonlinearOperator(f, :op_f)

julia> @objective(model, Min, bar(x))
op_f(x)

julia> bar(2.0)
4.0
```
