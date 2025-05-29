```
struct Match <: AbstractMatch
    syntax_node::JuliaSyntax.SyntaxNode
    captures::Vector{JuliaSyntax.SyntaxNode}
end
```

Represents a single match to a [`Pattern`](@ref), typically created from the `eachmatch` or `match` function.

The `syntax_node` field stores the `SyntaxNode` that matched the [`Pattern`](@ref) and the `captures` field stores the `SyntaxNode`s that fill match each wildcard in the [`Pattern`](@ref), indexed in the order they appear.

Methods that accept `Match` objects are defined for `Expr`, `SyntaxNode`, `AbstractString`, [`indices`](@ref), and `getindex`.

# Examples

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
