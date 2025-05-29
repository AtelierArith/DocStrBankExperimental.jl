```
struct Match <: AbstractMatch
    syntax_node::JuliaSyntax.SyntaxNode
    captures::Vector{JuliaSyntax.SyntaxNode}
end
```

[`Pattern`](@ref) に対する単一のマッチを表し、通常は `eachmatch` または `match` 関数から作成されます。

`syntax_node` フィールドは [`Pattern`](@ref) にマッチした `SyntaxNode` を格納し、`captures` フィールドは [`Pattern`](@ref) の各ワイルドカードにマッチする `SyntaxNode` を格納し、出現する順序でインデックス付けされています。

`Match` オブジェクトを受け入れるメソッドは `Expr`、`SyntaxNode`、`AbstractString`、[`indices`](@ref)、および `getindex` に対して定義されています。

# 例

```jldoctest
julia> m = match(j"√*", "2 + √ x")
CodeSearch.Match((call-pre √ x), captures=[x])

julia> m.captures
1-element Vector{JuliaSyntax.SyntaxNode}:
 x

julia> m[1]
line:col│ tree        │ file_name
   1:7  │x

julia> Expr(m)
:(√x)

julia> AbstractString(m)
" √ x"

julia> CodeSearch.indices(m)
4:9
```
