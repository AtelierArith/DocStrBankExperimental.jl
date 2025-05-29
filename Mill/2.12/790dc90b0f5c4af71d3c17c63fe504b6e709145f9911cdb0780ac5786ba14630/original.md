```
lens2code(n, l)
```

Convert [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) lens `l` to a `Vector` of codes from [`HierarchicalUtils.jl`](@ref) traversal such that they access each node in tree `n` egal to node accessible by lens `l`.

# Examples

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])));

julia> printtree(n; trav=true)
ProductNode [""]  2 obs
  ├── BagNode ["E"]  2 obs
  │     ╰── ∅ ["M"]
  ╰── ArrayNode(2×2 Array with Int64 elements) ["U"]  2 obs

julia> lens2code(n, (@optic _.data[2]))
1-element Vector{String}:
 "U"

julia> lens2code(n, (@optic _.data[∗]))
2-element Vector{String}:
 "E"
 "U"

```

See also: [`code2lens`](@ref).
