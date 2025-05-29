```
hardwiredcluster(edge::Edge, taxa::Union{AbstractVector{String},AbstractVector{Int}})
hardwiredcluster!(v::Vector{Bool}, edge::Edge, taxa)
hardwiredcluster!(v::Vector{Bool}, edge::Edge, taxa, visited::Vector{Int})
```

Calculate the hardwired cluster of `edge`, coded as a vector of booleans: true for taxa that are descendent of the edge, false for other taxa (including missing taxa).

The edge should belong in a rooted network for which `ischild1` is up-to-date. Run `directedges!` beforehand. This is very important, otherwise one might enter an infinite loop, and the function does not test for this.

visited: vector of node numbers, of all visited nodes.

# Examples:

```jldoctest
julia> net5 = "(A,((B,#H1),(((C,(E)#H2),(#H2,F)),(D)#H1)));" |> readnewick |> directedges! ;

julia> taxa = net5 |> tiplabels # ABC EF D
6-element Vector{String}:
 "A"
 "B"
 "C"
 "E"
 "F"
 "D"

julia> hardwiredcluster(net5.edge[12], taxa) # descendants of 12th edge = CEF
6-element Vector{Bool}:
 0
 0
 1
 1
 1
 0
```

See also [`hardwiredclusterdistance`](@ref) and [`hardwiredclusters`](@ref)
