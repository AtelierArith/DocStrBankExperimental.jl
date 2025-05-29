```
formulas(
    g::CompleteFlatGrammar{V,O} where {V,O};
    maxdepth::Integer,
    nformulas::Union{Nothing,Integer} = nothing
)::Vector{SyntaxBranch}
```

Generate all formulas whose `SyntaxBranch`s that are not taller than a given `maxdepth`.

See also [`AbstractGrammar`](@ref), [`SyntaxBranch`](@ref).
