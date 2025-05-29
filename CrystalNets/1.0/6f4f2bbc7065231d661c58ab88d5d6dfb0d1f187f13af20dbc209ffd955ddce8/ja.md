```
TopologicalGenome
```

`CrystalNets.jl`によって計算されたトポロジカルゲノム。

認識されている場合は、実際のゲノム（`PeriodicGraph`として）とネットの名前の両方を保存します。

`PeriodicGraph`のように、`TopologicalGenome`のテキスト表現は再び`TopologicalGenome`にパースできます：

```jldoctest
julia> topology = topological_genome(CrystalNet(PeriodicGraph("2  1 2 0 0  2 1 0 1  2 1 1 0")))
hcb

julia> typeof(topology)
TopologicalGenome

julia> PeriodicGraph(topology)  # 実際のトポロジカルゲノム、PeriodicGraphとして
PeriodicGraph2D(2, PeriodicEdge2D[(1, 2, (-1,0)), (1, 2, (0,0)), (1, 2, (0,1))])

julia> parse(TopologicalGenome, "hcb") == topology
true
```
