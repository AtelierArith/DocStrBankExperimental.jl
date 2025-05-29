```
set_optimizer_attributes(model::Model, pairs::Pair...)
```

Given a list of `attribute => value` pairs, calls `set_optimizer_attribute(model, attribute, value)` for each pair.

## Example

```julia
model = Model(Ipopt.Optimizer)
set_optimizer_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

is equivalent to:

```julia
model = Model(Ipopt.Optimizer)
set_optimizer_attribute(model, "tol", 1e-4)
set_optimizer_attribute(model, "max_iter", 100)
```

See also: [`set_optimizer_attribute`](@ref), [`get_optimizer_attribute`](@ref).
