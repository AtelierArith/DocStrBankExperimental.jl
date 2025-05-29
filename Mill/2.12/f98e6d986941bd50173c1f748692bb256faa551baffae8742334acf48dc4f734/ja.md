```
metadata_getindex(x, i::Integer)
metadata_getindex(x, i::VecOrRange{<:Integer})
```

メタデータ `x` にインデックスを付けます。 [`Mill.jl`](@ref) では、2番目または最後の次元が観測にインデックスを付けると仮定されています。これは、[`AbstractMillNode`](@ref) のカスタムサブタイプを実装する際に使用できます。

# 例

```jldoctest
julia> Mill.metadata_getindex(["foo", "bar", "baz"], 2)
"bar"

julia> Mill.metadata_getindex(["foo", "bar", "baz"], 2:3)
2-element Vector{String}:
 "bar"
 "baz"

julia> Mill.metadata_getindex([1 2 3; 4 5 6], 2)
2-element Vector{Int64}:
 2
 5

julia> Mill.metadata_getindex([1 2 3; 4 5 6], [1, 3])
2×2 Matrix{Int64}:
 1  3
 4  6
```

関連情報: [`Mill.metadata`](@ref), [`Mill.dropmeta`](@ref).
