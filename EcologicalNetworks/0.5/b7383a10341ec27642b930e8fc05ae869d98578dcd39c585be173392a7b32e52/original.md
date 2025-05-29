```
symmetry(N::AbstractUnipartiteNetwork)
```

Computes the symmetry between s^in and s^out (the in- and outgoing weighted degree of an unipartite network). This is computed as the Pearson correlation between the s^in and s^out. It is hence a value between -1 and 1, where high positive values indicate that species with many outgoing degrees tend to have many ingoing degrees and negative values mean the opposite. An undirected network is perfectly symmetric but, for example, a food web where predators are less likely to be prey would have a negative symmetry.

> Goa, J., Barzael, B. and Barabási 2016. Universal resilience patterns in complex networks. Nature 530(7590), 307-312. doi:10.1038/nature16948

