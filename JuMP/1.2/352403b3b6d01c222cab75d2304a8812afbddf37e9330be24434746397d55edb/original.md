```
Model(optimizer_factory; add_bridges::Bool = true)
```

Return a new JuMP model with the provided optimizer and bridge settings.

See [`set_optimizer`](@ref) for the description of the `optimizer_factory` and `add_bridges` arguments.

## Examples

Create a model with the optimizer set to `Ipopt`:

```julia
model = Model(Ipopt.Optimizer)
```

Pass an anonymous function which creates a `Gurobi.Optimizer`, and disable bridges:

```julia
env = Gurobi.Env()
model = Model(() -> Gurobi.Optimizer(env); add_bridges = false)
```
