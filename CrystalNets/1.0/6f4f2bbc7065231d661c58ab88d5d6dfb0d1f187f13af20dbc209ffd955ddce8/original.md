```
TopologicalGenome
```

A topological genome computed by `CrystalNets.jl`.

Store both the actual genome (as a `PeriodicGraph`) and the name of the net, if recognized.

Like for a `PeriodicGraph`, the textual representation of a `TopologicalGenome` can be parsed back into a `TopologicalGenome`:

```jldoctest
julia> topology = topological_genome(CrystalNet(PeriodicGraph("2  1 2 0 0  2 1 0 1  2 1 1 0")))
hcb

julia> typeof(topology)
TopologicalGenome

julia> PeriodicGraph(topology)  # The actual topological genome, as a PeriodicGraph
PeriodicGraph2D(2, PeriodicEdge2D[(1, 2, (-1,0)), (1, 2, (0,0)), (1, 2, (0,1))])

julia> parse(TopologicalGenome, "hcb") == topology
true
```
