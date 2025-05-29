```
code2lens(n, c)
```

Convert code `c` from [`HierarchicalUtils.jl`](@ref) traversal to a `Vector` of [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) lenses such that they access each node in tree `n` egal to node under code `c` in the tree.

# Examples

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])));

julia> printtree(n; trav=true)
ProductNode [""]  2 obs
  ├── BagNode ["E"]  2 obs
  │     ╰── ∅ ["M"]
  ╰── ArrayNode(2×2 Array with Int64 elements) ["U"]  2 obs

julia> code2lens(n, "U")
1-element Vector{Any}:
 (@o _.data[2])
```

See also: [`lens2code`](@ref).
