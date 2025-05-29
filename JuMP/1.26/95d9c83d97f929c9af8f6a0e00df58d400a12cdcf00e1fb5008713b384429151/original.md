```
BridgeableConstraint(
    constraint::C,
    bridge_type::B;
    coefficient_type::Type{T} = Float64,
) where {C<:AbstractConstraint,B<:Type{<:MOI.Bridges.AbstractBridge},T}
```

An [`AbstractConstraint`](@ref) representinng that `constraint` that can be bridged by the bridge of type `bridge_type{coefficient_type}`.

Adding a `BridgeableConstraint` to a model is equivalent to:

```julia
add_bridge(model, bridge_type; coefficient_type = coefficient_type)
add_constraint(model, constraint)
```

## Example

Given a new scalar set type `CustomSet` with a bridge `CustomBridge` that can bridge `F`-in-`CustomSet` constraints, when the user does:

```julia
model = Model()
@variable(model, x)
@constraint(model, x + 1 in CustomSet())
optimize!(model)
```

with an optimizer that does not support `F`-in-`CustomSet` constraints, the constraint will not be bridged unless they first call `add_bridge(model, CustomBridge)`.

In order to automatically add the `CustomBridge` to any model to which an `F`-in-`CustomSet` is added, add the following method:

```julia
function JuMP.build_constraint(
    error_fn::Function,
    func::AbstractJuMPScalar,
    set::CustomSet,
)
    constraint = ScalarConstraint(func, set)
    return BridgeableConstraint(constraint, CustomBridge)
end
```

## Note

JuMP extensions should extend `JuMP.build_constraint` only if they also defined `CustomSet`, for three reasons:

1. It is problematic if multiple extensions overload the same JuMP method.
2. A missing method will not inform the users that they forgot to load the extension module defining the `build_constraint` method.
3. Defining a method where neither the function nor any of the argument types are defined in the package is called [*type piracy*](https://docs.julialang.org/en/v1/manual/style-guide/index.html#Avoid-type-piracy-1) and is discouraged in the Julia style guide.
