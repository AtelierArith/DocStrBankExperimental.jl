```
function randframe(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Int64,
    nedges::Int64,
    facts::Vector{SyntaxLeaf}
end
```

Return a random Kripke Frame, which is a directed graph interpreted as a [`SoleLogics.ExplicitCrispUniModalFrame`](@ref). The underlying graph is generated using [`Graphs.SimpleGraphs.SimpleDiGraph`](@ref).

# Arguments:

  * `rng` is a random number generator, or the seed used to create one;
  * `nworld` is the number of worlds (nodes) in the frame. Worlds are numbered from `1`   to `nworld` included.
  * `nedges` is the number of relations (edges) in the frame;
  * `facts` is a vector of generic [`SyntaxLeaf`](@ref).

See also [`SyntaxLeaf`](@ref), [`Graphs.SimpleGraphs.SimpleDiGraph`](@ref), [`SoleLogics.ExplicitCrispUniModalFrame`](@ref).
