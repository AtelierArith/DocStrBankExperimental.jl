```julia
read_td_file(
    td_filepath::AbstractString
) -> Tuple{Int64, Int64, Int64, Vector{Vector{Int64}}, Vector{Vector{Int64}}}

```

Parse a tree decomposition instance described the PACE format.

The PACE file format is defined in: https://pacechallenge.org/2017/treewidth/
