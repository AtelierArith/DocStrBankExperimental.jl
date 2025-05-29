```
struct BaseLogic{G<:AbstractGrammar,A<:AbstractAlgebra} <: AbstractLogic{G,A}
    grammar::G
    algebra::A
end
```

A basic logic based on a grammar and an algebra, where both the grammar and the algebra are instantiated.

See also [`grammar`](@ref), [`algebra`](@ref), [`AbstractGrammar`](@ref), [`AbstractAlgebra`](@ref), [`AbstractLogic`](@ref).
