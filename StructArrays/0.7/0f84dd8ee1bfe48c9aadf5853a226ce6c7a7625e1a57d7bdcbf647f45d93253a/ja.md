```
StructArrays.replace_storage(f, s::StructArray)
```

コンポーネントのストレージタイプを変更します：各配列 `v` は `f(v)` に置き換えられます。`f(v)` は `v` と同じ `eltype` と `size` を持つことが期待されます。

## 例

PooledArrays がロードされている場合、非 `isbitstype` のすべての列をプールできます：

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
