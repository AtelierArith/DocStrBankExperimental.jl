```
direct_model(factory::MOI.OptimizerWithAttributes)
```

Create a [`direct_model`](@ref) using `factory`, a `MOI.OptimizerWithAttributes` object created by [`optimizer_with_attributes`](@ref).

## Example

```julia
model = direct_model(
    optimizer_with_attributes(
        Gurobi.Optimizer,
        "Presolve" => 0,
        "OutputFlag" => 1,
    )
)
```

is equivalent to:

```julia
model = direct_model(Gurobi.Optimizer())
set_optimizer_attribute(model, "Presolve", 0)
set_optimizer_attribute(model, "OutputFlag", 1)
```
