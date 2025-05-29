```
ProductNode(dss, m=nothing)
ProductNode(m=nothing; dss...)
```

データ `dss` とメタデータ `m` を持つ新しい [`ProductNode`](@ref) を構築します。

`dss` は `Tuple` または `NamedTuple` である必要があり、そのすべての要素は同じ数の観測値を含む必要があります。

`dss` のいずれかの要素が [`AbstractMillNode`](@ref) でない場合、それは最初に [`ArrayNode`](@ref) にラップされます。

# 例

```jldoctest
julia> ProductNode((ArrayNode(zeros(2, 2)), ArrayNode(Flux.onehotbatch([1, 2], 1:2))))
ProductNode  2 obs
  ├── ArrayNode(2×2 Array with Float64 elements)  2 obs
  ╰── ArrayNode(2×2 OneHotArray with Bool elements)  2 obs

julia> ProductNode(x1 = ArrayNode(NGramMatrix(["Hello", "world"])),
                   x2 = BagNode(ArrayNode([1 2; 3 4]), [1:2, 0:-1]))
ProductNode  2 obs
  ├── x1: ArrayNode(2053×2 NGramMatrix with Int64 elements)  2 obs
  ╰── x2: BagNode  2 obs
            ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> ProductNode([1 2 3])
ProductNode  3 obs
  ╰── ArrayNode(1×3 Array with Int64 elements)  3 obs

julia> ProductNode((ArrayNode([1 2; 3 4]), ArrayNode([1 2 3; 4 5 6])))
ERROR: AssertionError: All subtrees must have an equal amount of instances!
[...]
```

参照: [`AbstractProductNode`](@ref), [`AbstractMillNode`](@ref), [`ProductModel`](@ref).
