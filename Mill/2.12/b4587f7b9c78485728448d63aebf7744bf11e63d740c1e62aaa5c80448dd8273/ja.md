```
Mill.unpack2mill(x::LazyNode)
```

[`LazyNode`](@ref) `x`の表現を[`Mill.jl`](https://github.com/CTUAvastLab/Mill.jl)の構造を使用して返します。すべてのカスタム[`LazyNode`](@ref)は、[`LazyModel`](@ref)で使用されるため、特別なメソッドを持つ必要があります。

# 例

```julia-repl
julia> function Mill.unpack2mill(ds::LazyNode{:Sentence})
    s = split.(ds.data, " ")
    x = NGramMatrix(reduce(vcat, s))
    BagNode(x, Mill.length2bags(length.(s)))
end;
```

```jldoctest
julia> LazyNode{:Sentence}(["foo bar", "baz"]) |> Mill.unpack2mill
BagNode  2 obs
  ╰── ArrayNode(2053×3 NGramMatrix with Int64 elements)  3 obs
```

参照: [`LazyNode`](@ref), [`LazyModel`](@ref).
