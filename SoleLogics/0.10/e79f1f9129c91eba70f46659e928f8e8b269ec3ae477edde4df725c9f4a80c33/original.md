```
function randmodel(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Integer,
    nedges::Integer,
    facts::Vector{SyntaxLeaf};
    truthvalues::Union{AbstractAlgebra,AbstractVector{<:Truth}}
)
```

# Arguments

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: random number generator;
  * `nworlds::Int64`: number of worlds (nodes) in the frame (numbered from `1` to `nworld`   included).
  * `nedges::Int64`: number of relations (edges) in the frame;
  * `facts::Int64`: vector of generic [`SyntaxLeaf`](@ref), representing facts to which a certain   valuation function can associate a [`Truth`](@ref) value;
  * `truthvalues::Union{AbstractAlgebra,AbstractVector{<:Truth}}`: [`Truth`](@ref) values to   be associated for each element of `facts`.

# Examples

```julia-repl
julia> randmodel(Random.MersenneTwister(42),5,10, [Atom("s"), Atom("p")], BooleanAlgebra())
KripkeStructure{SoleLogics.ExplicitCrispUniModalFrame{SoleLogics.World{Int64}, Graphs.SimpleGraphs.SimpleDiGraph{Int64}}, Dict{SoleLogics.World{Int64}, TruthDict{Dict{Atom{String}, BooleanTruth}}}} with
- frame = SoleLogics.ExplicitCrispUniModalFrame{SoleLogics.World{Int64}, Graphs.SimpleGraphs.SimpleDiGraph{Int64}} with
- worlds = ["1", "2", "3", "4", "5"]
- accessibles =
        1 -> [2, 3, 5]
        2 -> [1, 4, 5]
        3 -> []
        4 -> [1, 2]
        5 -> [1, 2]
- valuations =
        1 -> TruthDict([s => ⊥, p => ⊤])
        2 -> TruthDict([s => ⊥, p => ⊥])
        3 -> TruthDict([s => ⊥, p => ⊥])
        4 -> TruthDict([s => ⊤, p => ⊤])
        5 -> TruthDict([s => ⊤, p => ⊤])
```

See also [`AbstractAlgebra`](@ref), [`SyntaxLeaf`](@ref), [`Truth`](@ref).
