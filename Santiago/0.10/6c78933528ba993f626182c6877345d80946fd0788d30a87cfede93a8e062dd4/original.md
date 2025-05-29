```julia
dot_string(sys::Santiago.System) -> String
dot_string(
    sys::Santiago.System,
    no_group::Array{String}
) -> String
dot_string(
    sys::Santiago.System,
    no_group::Array{String},
    options::String
) -> String

```

Returns a `String``representing`System` in the GraphViz's dot format.

## Arguments

  * `no_group`: Array of functional groups which should not be grouped in the plot
  * `options`: String of *graphviz* options

```

```
