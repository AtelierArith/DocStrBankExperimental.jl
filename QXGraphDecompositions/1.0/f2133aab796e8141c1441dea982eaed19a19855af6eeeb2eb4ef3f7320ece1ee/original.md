```
restricted_mcs(H::LabeledGraph, C::Array{Symbol, 1})
```

Return an elimination order for the chordal graph 'H' with the vertices in 'C' appearing at  the end.

If the chordal graph `H` was created from an elimination order π for a graph `G`, the  returned elimination order for `H` will have a treewidth equal to that of π if `C` is a clique in `H`.

The algorithm is described by Shutski et al in https://arxiv.org/abs/1911.12242
