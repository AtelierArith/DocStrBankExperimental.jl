```
JuMP.set_optimizer_attributes(model::InfiniteModel, pairs::Pair...)
```

Extend `set_optimizer_attributes` to set multiple solver attributes given a  list of `attribute => value` pairs. Calls  `set_optimizer_attribute(model, attribute, value)` for each pair.

**Example**

```julia-repl
julia> model = Model(Ipopt.Optimizer);

julia> set_optimizer_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

is equivalent to:

```julia-repl
julia> set_optimizer_attribute(model, "tol", 1e-4);

julia> set_optimizer_attribute(model, "max_iter", 100);
```
