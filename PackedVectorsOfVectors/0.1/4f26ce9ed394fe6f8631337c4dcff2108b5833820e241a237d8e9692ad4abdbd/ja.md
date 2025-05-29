```
pack([T,] vv) -> PackedVectorOfVectors
```

ベクトルのベクトル `vv` をそのパックされた表現に変換します。`T` が提供されている場合、ネストされたベクトルの要素はこの型に変換されます。

# 例

```jldoctest
julia> pack([[1,2],[3]])
2-element pack(::Vector{Vector{Int64}}):
 [1, 2]
 [3]

julia> pack(Float64, [[1,2],[3]])
2-element pack(::Vector{Vector{Float64}}):
 [1.0, 2.0]
 [3.0]
```
