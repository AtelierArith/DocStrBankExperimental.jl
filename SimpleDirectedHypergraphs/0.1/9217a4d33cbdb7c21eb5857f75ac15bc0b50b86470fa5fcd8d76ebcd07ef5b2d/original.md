```
to_undirected(h::DirectedHypergraph)
```

Converts a directed hypergraph into an undirected hypergraph. Tail and head hyperedges are combined; that is, for all hyperedges he*orig in the directed hypergraph h, all vertices in the head or tail are added to a corresponding undirected hyperedge he*new in the undirected hypergraph h'.

Metadata is combined into tuples; i.e., if there was originally tail metadata t*meta and head metadata h*meta for a given directed hyperedge, the new undirected hyperedge will have metadata (t*meta, h*meta).

Because vertex-hyperedge weights are restricted to real numbers, we cannot combine the weights, so we simply set the values to 1.0 if a given vertex is in a given hyperedge 
