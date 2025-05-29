```
function randformula(
    [T::Type{<:Formula}=SyntaxTree,]
    [rng::Union{Integer,AbstractRNG}=Random.GLOBAL_RNG,]
    maxheight::Integer,
    [g::AbstractGrammar,]
    args...;
    kwargs...
)
```

Fallback to `randformula`, specifying only the `maxheight` (possibly also a `grammar`) of the generated [`SyntaxTree`](@ref).

See also [`AbstractGrammar`](@ref), [`randformula(::Integer, ::Union{AbstractVector,AbstractAlphabet}, ::AbstractVector)`](@ref).
