```
find_lens(n, x)
```

`n`内のすべてのノード/フィールドにアクセスするための`Vector`を返します。これらは、`Base.===`を使用して`x`と比較したときに`true`を返します。

# 例

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

関連情報: [`pred_lens`](@ref), [`list_lens`](@ref), [`findnonempty_lens`](@ref).
