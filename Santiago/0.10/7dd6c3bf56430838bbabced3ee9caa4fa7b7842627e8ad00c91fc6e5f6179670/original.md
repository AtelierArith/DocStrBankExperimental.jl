```julia
dot_file(sys::Santiago.System, file::AbstractString)
dot_file(
    sys::Santiago.System,
    file::AbstractString,
    no_group::Array{String}
)
dot_file(
    sys::Santiago.System,
    file::AbstractString,
    no_group::Array{String},
    options::String
)

```

Writes a DOT file of a `System`. The resulting file can be visualized with GraphViz, e.g.:  `dot -Tpng file.dot -o graph.png`

## Arguments

  * `no_group`: Array of functional groups which should not be grouped in the plot
  * `options`: String of *graphviz* options

```

```
