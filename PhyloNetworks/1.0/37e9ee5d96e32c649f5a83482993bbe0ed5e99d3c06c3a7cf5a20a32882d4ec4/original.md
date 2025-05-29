```
nni!([rng::AbstractRNG,]
     net::HybridNetwork,
     e::Edge,
     nohybridladder::Bool=true,
     no3cycle::Bool=true,
     constraints::Vector{TopologyConstraint}=TopologyConstraint[]
)
```

Attempt to perform a nearest neighbor interchange (NNI) around edge `e`, randomly chosen among all possible NNIs (e.g 3, sometimes more depending on `e`) satisfying the constraints, and such that the new network is a DAG. The number of possible NNI moves around an edge depends on whether the edge's parent/child nodes are tree or hybrid nodes. This is calculated by [`nnimax`](@ref).

The option `no3cycle` forbids moves that would create a 3-cycle in the network. When `no3cycle` = false, 2-cycle and 3-cycles may be generated.

Note that the defaults values are for positional (not keyword) arguments, so two or more arguments can be used, but in a specific order: `nni!(net, e)` or `nni!(net, e, nohybridladder)`, `nni!(net, e, nohybridladder, no3cycle)`, `nni!(net, e, nohybridladder, no3cycle, contraints)`.

Assumptions:

  * The starting network does not have 3-cycles, if `no3cycle=true`. No check for the presence of 2- and 3-cycles in the input network.
  * The edges' field `ischild1` is correct in the input network. (This field will be correct in the output network.)

Output: information indicating how to undo the move or `nothing` if all NNIs failed.

# examples

```jldoctest
julia> str_network = "(((S8,S9),(((((S1,S2,S3),S4),(S5)#H1),(#H1,(S6,S7))))#H2),(#H2,S10));";

julia> net = readnewick(str_network);

julia> # using Random; Random.seed!(3); ## commented out for doctest reproducibility across julia versions, but users can use this line to set the seed in their analyses.

julia> undoinfo = nni!(net, net.edge[3], true, true); # true's to avoid hybrid ladders and 3-cycles
```

In the next example, we use a stable RNG to make the example reproducible across julia versions. However, this particular RNG is *not* recommended. The RNG used by default is better (e.g. much more efficient).

```jldoctest nni
julia> str_network = "(((S8,S9),(((((S1,S2,S3),S4),(S5)#H1),(#H1,(S6,S7))))#H2),(#H2,S10));";

julia> net = readnewick(str_network);

julia> # using Pkg; Pkg.add("StableRNGs") # to install StableRNGs if not done earlier

julia> using StableRNGs

julia> rng = StableRNG(791);

julia> undoinfo = nni!(rng, net, net.edge[3], true, true); # true's to avoid hybrid ladders and 3-cycles

julia> writenewick(net)
"((S9,((((((S1,S2,S3),S4),(S5)#H1),(#H1,(S6,S7))))#H2,S8)),(#H2,S10));"

julia> nni!(undoinfo...);

julia> writenewick(net) == str_network # net back to original topology: the NNI was "undone"
true
```
