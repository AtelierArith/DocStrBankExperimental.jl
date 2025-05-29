```
negative_sample(g::GNNGraph; 
                num_neg_edges = g.num_edges, 
                bidirected = is_bidirected(g))
```

Return a graph containing random negative edges (i.e. non-edges) from graph `g` as edges.

If `bidirected=true`, the output graph will be bidirected and there will be no leakage from the origin graph. 

See also [`is_bidirected`](@ref).
