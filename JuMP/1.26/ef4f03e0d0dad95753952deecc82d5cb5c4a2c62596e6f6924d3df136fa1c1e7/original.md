```
set_attributes(
    destination::Union{
        GenericModel,
        MOI.OptimizerWithAttributes,
        GenericVariableRef,
        ConstraintRef,
    },
    pairs::Pair...,
)
```

Given a list of `attribute => value` pairs, calls `set_attribute(destination, attribute, value)` for each pair.

See also: [`set_attribute`](@ref), [`get_attribute`](@ref).

## Example

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

is equivalent to:

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_attribute(model, "tol", 1e-4)

julia> set_attribute(model, "max_iter", 100)
```
