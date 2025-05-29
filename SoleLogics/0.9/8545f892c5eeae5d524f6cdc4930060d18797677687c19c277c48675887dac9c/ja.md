```
formulas(
    g::CompleteFlatGrammar{V,O} where {V,O};
    maxdepth::Integer,
    nformulas::Union{Nothing,Integer} = nothing
)::Vector{SyntaxBranch}
```

与えられた `maxdepth` よりも高くない `SyntaxBranch` のすべての式を生成します。

また、[`AbstractGrammar`](@ref)、[`SyntaxBranch`](@ref)も参照してください。
