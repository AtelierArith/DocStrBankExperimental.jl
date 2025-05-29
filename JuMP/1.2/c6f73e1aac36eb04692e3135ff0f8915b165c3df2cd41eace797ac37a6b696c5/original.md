```
optimizer_with_attributes(optimizer_constructor, attrs::Pair...)
```

Groups an optimizer constructor with the list of attributes `attrs`. Note that it is equivalent to `MOI.OptimizerWithAttributes`.

When provided to the `Model` constructor or to [`set_optimizer`](@ref), it creates an optimizer by calling `optimizer_constructor()`, and then sets the attributes using [`set_optimizer_attribute`](@ref).

## Example

```julia
model = Model(
    optimizer_with_attributes(
        Gurobi.Optimizer, "Presolve" => 0, "OutputFlag" => 1
    )
)
```

is equivalent to:

```julia
model = Model(Gurobi.Optimizer)
set_optimizer_attribute(model, "Presolve", 0)
set_optimizer_attribute(model, "OutputFlag", 1)
```

## Note

The string names of the attributes are specific to each solver. One should consult the solver's documentation to find the attributes of interest.

See also: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).
