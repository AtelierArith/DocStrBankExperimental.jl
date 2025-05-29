```
list_lens(n)
```

Return a `Vector` of [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) lenses for accessing all nodes/fields in `n`.

# Examples

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])))
ProductNode  2 obs
  ├── BagNode  2 obs
  │     ╰── ∅
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> list_lens(n)
9-element Vector{Any}:
 identity (generic function with 1 method)
 (@o _.data[1])
 (@o _.data[1].data)
 (@o _.data[1].bags)
 (@o _.data[1].metadata)
 (@o _.data[2])
 (@o _.data[2].data)
 (@o _.data[2].metadata)
 (@o _.metadata)
```

See also: [`pred_lens`](@ref), [`find_lens`](@ref), [`findnonempty_lens`](@ref).
