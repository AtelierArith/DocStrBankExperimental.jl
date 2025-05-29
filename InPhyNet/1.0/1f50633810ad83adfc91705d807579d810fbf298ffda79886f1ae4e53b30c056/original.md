Returns a list of networks where each entry is a copy of `net` pruned to include only the taxa named in each subset contained in `subsets`. `subsets` can also be an individual vector of strings instead of a nested vector (see examples below).

# Example

```julia
net = readnewick("((t1,t2),(t3,t4));")
prune_network(net, [["t1", "t2"], ["t3", "t4"]])
> 2-element Vector{HybridNetwork}: (t1, t2); and (t3, t4);

prune_network(net, ["t1", "t2", "t3"])
```
