```
struct BridgeableConstraint{C, B} <: AbstractConstraint
    constraint::C
    bridge_type::B
end
```

Constraint `constraint` that can be bridged by the bridge of type `bridge_type`. Adding this constraint to a model is equivalent to

```julia
add_bridge(model, bridge_type)
add_constraint(model, constraint)
```

## Examples

Given a new scalar set type `CustomSet` with a bridge `CustomBridge` that can bridge `F`-in-`CustomSet` constraints, when the user does

```julia
model = Model()
@variable(model, x)
@constraint(model, x + 1 in CustomSet())
optimize!(model)
```

with an optimizer that does not support `F`-in-`CustomSet` constraints, the constraint will not be bridged unless he manually calls `add_bridge(model, CustomBridge)`. In order to automatically add the `CustomBridge` to any model to which an `F`-in-`CustomSet` is added, simply add the following method:

```julia
function JuMP.build_constraint(_error::Function, func::AbstractJuMPScalar,
                               set::CustomSet)
    constraint = ScalarConstraint(func, set)
    return JuMP.BridgeableConstraint(constraint, CustomBridge)
end
```

### Note

JuMP extensions should extend `JuMP.build_constraint` only if they also defined `CustomSet`, for three reasons:

1. It is problematic if multiple extensions overload the same JuMP method.
2. A missing method will not inform the users that they forgot to load the extension module defining the `build_constraint` method.
3. Defining a method where neither the function nor any of the argument types are defined in the package is called [*type piracy*](https://docs.julialang.org/en/v1/manual/style-guide/index.html#Avoid-type-piracy-1) and is discouraged in the Julia style guide.
