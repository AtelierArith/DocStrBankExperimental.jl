```
code2lens(n, c)
```

コード `c` を [`HierarchicalUtils.jl`](@ref) のトラバーサルから `Vector` の [`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) レンズに変換し、これにより木 `n` の各ノードにアクセスできるようにします。これは、木の中のコード `c` に対応するノードに等しいです。

# 例

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

関連情報: [`lens2code`](@ref).
