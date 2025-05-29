```
function randformula(
    [T::Type{<:Formula}=SyntaxTree,]
    [rng::Union{Integer,AbstractRNG}=Random.GLOBAL_RNG,]
    height::Integer,
    [g::AbstractGrammar,]
    args...;
    kwargs...
)
```

生成された[`SyntaxTree`](@ref)の`height`（おそらく`grammar`も）だけを指定して`randformula`にフォールバックします。

[`AbstractGrammar`](@ref)や[`randformula(::Integer, ::Union{AbstractVector,AbstractAlphabet}, ::AbstractVector)`](@ref)も参照してください。
