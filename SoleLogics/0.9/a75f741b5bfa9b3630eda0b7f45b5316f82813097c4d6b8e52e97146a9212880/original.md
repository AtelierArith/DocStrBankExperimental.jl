```
function check(
    φ::SyntaxTree,
    i::AbstractKripkeStructure,
    w::Union{Nothing,AnyWorld,<:AbstractWorld} = nothing;
    use_memo::Union{Nothing,AbstractDict{<:Formula,<:Vector{<:AbstractWorld}}} = nothing,
    perform_normalization::Bool = true,
    memo_max_height::Union{Nothing,Int} = nothing,
)::Bool
```

Check a formula on a specific word in a [`KripkeStructure`](@ref).

# Examples

```julia-repl
julia> using Graphs, Random

julia> @atoms String p q
2-element Vector{Atom{String}}:
 Atom{String}("p")
 Atom{String}("q")

julia> fmodal = randformula(Random.MersenneTwister(14), 3, [p,q], SoleLogics.BASE_MODAL_CONNECTIVES)
¬□(p ∨ q)

# A special graph, called Kripke Frame, is created.
# Nodes are called worlds, and the edges are relations between worlds.
julia> worlds = SoleLogics.World.(1:5) # 5 worlds are created, numerated from 1 to 5

julia> edges = Edge.([(1,2), (1,3), (2,4), (3,4), (3,5)])

julia> kframe = SoleLogics.ExplicitCrispUniModalFrame(worlds, Graphs.SimpleDiGraph(edges))

# A valuation function establishes which fact are true on each world
julia> valuation = Dict([
    worlds[1] => TruthDict([p => true, q => false]),
    worlds[2] => TruthDict([p => true, q => true]),
    worlds[3] => TruthDict([p => true, q => false]),
    worlds[4] => TruthDict([p => false, q => false]),
    worlds[5] => TruthDict([p => false, q => true]),
 ])

# Kripke Frame and valuation function are merged in a Kripke Structure
julia> kstruct = KripkeStructure(kframe, valuation)

julia> [w => check(fmodal, kstruct, w) for w in worlds]
5-element Vector{Pair{SoleLogics.World{Int64}, Bool}}:
 SoleLogics.World{Int64}(1) => 0
 SoleLogics.World{Int64}(2) => 1
 SoleLogics.World{Int64}(3) => 1
 SoleLogics.World{Int64}(4) => 0
 SoleLogics.World{Int64}(5) => 0
```

See also [`SyntaxTree`](@ref), [`AbstractWorld`](@ref), [`KripkeStructure`](@ref).
