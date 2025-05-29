```
find_lens(n, x)
```

Return a `Vector` of [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) lenses for accessing all nodes/fields in `n` that return `true` when compared to `x` using `Base.===`.

# Examples

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])))
ProductNode  2 obs
  ├── BagNode  2 obs
  │     ╰── ∅
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> find_lens(n, n.data[1])
1-element Vector{Any}:
 (@o _.data[1])
```

See also: [`pred_lens`](@ref), [`list_lens`](@ref), [`findnonempty_lens`](@ref).
