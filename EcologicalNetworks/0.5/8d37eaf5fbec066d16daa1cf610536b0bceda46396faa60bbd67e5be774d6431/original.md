```
heterogeneity(N::AbstractUnipartiteNetwork)
```

Computes the heterogeneity for an unipartite network, a topological characteristic which quantifies the difference in in- and outgoing degrees between species. It is computed as σ*in * σ*out / s_mean. A value of 0 indicates that all species have the same (weighted) in- and outdegrees.

> Goa, J., Barzael, B. and Barabási 2016. Universal resilience patterns in complex networks. Nature 530(7590), 307-312. doi:10.1038/nature16948

