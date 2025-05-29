```
findnonempty_lens(n)
```

Return a `Vector` of [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) lenses for accessing all nodes/fields in `n` that contain at least one observation.

# Examples

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])))
ProductNode  2 obs
  ├── BagNode  2 obs
  │     ╰── ∅
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> findnonempty_lens(n)
3-element Vector{Any}:
 identity (generic function with 1 method)
 (@o _.data[1])
 (@o _.data[2])
```

See also: [`pred_lens`](@ref), [`list_lens`](@ref), [`find_lens`](@ref).
