```
rydberg_density_sum([f], reg_or_samples)
```

Sum of rydberg density.

# Arguments

  * `f`: optional, postprocessing callback function `f(config) -> config`.   The input `config` is an integer of type `Int`, the output   `config` can be a type supports [`count_vertices`](@ref)   e.g, an `AbstractVector` or an `Integer`.
  * `reg_or_samples` can be a register (`Yao.ArrayReg` or [`SubspaceArrayReg`](@ref))   or a list of measurement result (config) in `AbstractVector`.

# Example

To implement the postprocessing protocal in MIS experiment:

1. calculating `rydberg_density_sum` by first reducing the configuration

to independent set using [`to_independent_set`](@ref)

2. randomly adding vertices then pick the largest [`count_vertices`](@ref)

using [`add_random_vertices`](@ref).

```julia
rydberg_density_sum(r) do config
    config = to_independent_set(config, graph)
    add_random_vertices(config, graph, 10)
    return config
end
```

Or one can also just add vertice by atom order

```julia
rydberg_density_sum(r) do config
    config = to_independent_set(config, graph)
    add_vertices!(config, graph)
    return config
end
```
