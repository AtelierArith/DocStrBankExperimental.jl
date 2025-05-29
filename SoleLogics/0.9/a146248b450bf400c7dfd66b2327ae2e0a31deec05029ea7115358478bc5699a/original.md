```
function randmodel(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Int64,
    nedges::Int64,
    facts::Vector{SyntaxLeaf};
    truthvalues::Union{AbstractAlgebra,AbstractVector{<:Truth}} = BooleanAlgebra();
    rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG
)
```
