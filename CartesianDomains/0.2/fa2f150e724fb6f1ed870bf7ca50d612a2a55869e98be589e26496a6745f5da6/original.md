```
edge_regions(full_domain::CartesianIndices, axis::Int, nhalo::Int, nedge::Int)
```

Extract the subdomains from `full_domain` along the boundaries of the halo region (defined by a thickness of `nhalo`), with a thickness of `nedge`.
