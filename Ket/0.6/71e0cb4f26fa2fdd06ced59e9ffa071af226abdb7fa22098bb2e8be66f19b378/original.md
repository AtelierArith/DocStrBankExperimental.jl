```
state_grid([T=ComplexF64], dA::Integer, dB::Integer, edges::Vector{Vector{ntuple{2, Int}}}; weights::Vector{T} = ones(T, length(edges)))
```

Produces the bipartite `dA` × `dB` grid state according to the `dA` × `dB` 2D (hyper-)graph with `edges` and `weights`.

Reference:

  * Lockhart et al., [arXiv:1705.09261](http://arxiv.org/abs/1705.09261)
  * Ghimire et al., [arXiv:2207.09826](https://arxiv.org/abs/2207.09826)
