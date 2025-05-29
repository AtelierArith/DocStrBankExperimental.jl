```julia
variable_dependencies(sys::AbstractSystem; variables = states(sys),
                      variablestoids = nothing)
```

For each variable, determine the equations that modify it and return as a [`BipartiteGraph`](@ref).

Notes:

  * Dependencies are returned as a [`BipartiteGraph`](@ref) mapping variable indices to the indices of equations that modify them.
  * `variables` denotes the list of variables to determine dependencies for.
  * `variablestoids` denotes a `Dict` mapping `Variable`s to their `Int` index in `variables`.

Example: Continuing the example of [`equation_dependencies`](@ref)

```julia
variable_dependencies(jumpsys)
```
