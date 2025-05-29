```
function randframe(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Integer,
    nedges::Integer,
end
```

Return a random Kripke Frame, which is a directed graph interpreted as a [`SoleLogics.ExplicitCrispUniModalFrame`](@ref). The underlying graph is generated using [`Graphs.SimpleGraphs.SimpleDiGraph`](@ref).

# Arguments

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: random number generator;
  * `nworlds::Int64`: number of worlds (nodes) in the frame (numbered from `1` to `nworld`   included).
  * `nedges::Int64`: number of relations (edges) in the frame;

# Examples

```julia-repl
julia> randframe(Random.MersenneTwister(42),5,10)
SoleLogics.ExplicitCrispUniModalFrame{SoleLogics.World{Int64}, Graphs.SimpleGraphs.SimpleDiGraph{Int64}} with
- worlds = ["1", "2", "3", "4", "5"]
- accessibles =
        1 -> [2, 3, 5]
        2 -> [1, 4, 5]
        3 -> []
        4 -> [1, 2]
        5 -> [1, 2]
```

See also [`SoleLogics.ExplicitCrispUniModalFrame`](@ref), [`SyntaxLeaf`](@ref), [`Graphs.SimpleGraphs.SimpleDiGraph`](@ref).
