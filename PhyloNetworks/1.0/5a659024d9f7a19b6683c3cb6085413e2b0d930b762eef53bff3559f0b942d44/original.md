```
treeedges_support(sample_net::Vector{HybridNetwork}, ref_net::HybridNetwork)`
```

Read a sample of networks `sample_net` (such as a bootstrap sample or a posterior sample) and a reference network (`ref_net`), and calculate the support for the tree edges in the reference network. All minor hybrid edges (γ<0.5) are removed to extract the major tree from each network. All remaining edges are tree edges, each associated with a bipartition.

output:

  * a data frame with one row per tree edge and two columns: edge number, bootstrap support (as a percentage)
  * the major tree from the reference network, where minor hybrid edges (with γ<0.5) have been removed.
