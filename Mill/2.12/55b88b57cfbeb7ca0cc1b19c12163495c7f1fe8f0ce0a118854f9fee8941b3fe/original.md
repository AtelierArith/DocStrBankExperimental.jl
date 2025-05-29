```
pred_lens(p, n)
```

Return a `Vector` of [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) lenses for accessing all nodes/fields in `n` conforming to predicate `p`.

# Examples

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])))
ProductNode  2 obs
  ├── BagNode  2 obs
  │     ╰── ∅
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> pred_lens(x -> x isa ArrayNode, n)
1-element Vector{Any}:
 (@o _.data[2])
```

See also: [`list_lens`](@ref), [`find_lens`](@ref), [`findnonempty_lens`](@ref).
