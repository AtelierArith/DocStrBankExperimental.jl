```
lens2code(n, l)
```

[`Accessors.jl`](https://github.com/JuliaObjects/Accessors.jl) レンズ `l` を、ツリー `n` の各ノードにアクセスするための [`HierarchicalUtils.jl`](@ref) トラバーサルからのコードの `Vector` に変換します。これは、レンズ `l` によってアクセス可能なノードに等しいです。

# 例

```jldoctest
julia> n = ProductNode((BagNode(missing, bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])));

julia> printtree(n; trav=true)
ProductNode [""]  2 obs
  ├── BagNode ["E"]  2 obs
  │     ╰── ∅ ["M"]
  ╰── ArrayNode(2×2 Array with Int64 elements) ["U"]  2 obs

julia> lens2code(n, (@optic _.data[2]))
1-element Vector{String}:
 "U"

julia> lens2code(n, (@optic _.data[∗]))
2-element Vector{String}:
 "E"
 "U"

```

参照: [`code2lens`](@ref).
