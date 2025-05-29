```
StructArrays.replace_storage(f, s::StructArray)
```

Change storage type for components: each array `v` is replaced by `f(v)`. `f(v)` is expected to have the same `eltype` and `size` as `v`.

## Examples

If PooledArrays is loaded, we can pool all columns of non `isbitstype`:

```jldoctest
julia> using StructArrays, PooledArrays

julia> s = StructArray(a=1:3, b = fill("string", 3));

julia> s_pooled = StructArrays.replace_storage(s) do v
           isbitstype(eltype(v)) ? v : convert(PooledArray, v)
       end
3-element StructArray(::UnitRange{Int64}, ::PooledVector{String, UInt32, Vector{UInt32}}) with eltype @NamedTuple{a::Int64, b::String}:
 (a = 1, b = "string")
 (a = 2, b = "string")
 (a = 3, b = "string")
```
