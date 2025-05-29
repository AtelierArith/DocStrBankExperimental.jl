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

`randformula`にフォールバックし、生成される[`SyntaxTree`](@ref)の`maxheight`（場合によっては`grammar`も）だけを指定します。

[`AbstractGrammar`](@ref)、[`randformula(::Integer, ::Union{AbstractVector,AbstractAlphabet}, ::AbstractVector)`](@ref)も参照してください。
