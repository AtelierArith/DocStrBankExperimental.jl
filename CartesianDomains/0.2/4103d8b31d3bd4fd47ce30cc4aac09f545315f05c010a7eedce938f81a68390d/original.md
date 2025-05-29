```
upper_edge_region(full_domain::CartesianIndices, axis::Int, nhalo::Int, nedge::Int)
```

Extract the subdomain from `full_domain` along the high edge of the inner domain with  a width of `nedge` along a given `axis`. The inner domain is the domain within `full_domain` that does not include the halo region. This function is designed to provide edges along the inner domain of a given width. This is useful for splitting a problem into domains in the "center" and domains along the edge.
