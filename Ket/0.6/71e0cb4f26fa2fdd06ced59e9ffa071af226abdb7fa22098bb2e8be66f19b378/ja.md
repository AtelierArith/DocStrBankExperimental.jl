```
state_grid([T=ComplexF64], dA::Integer, dB::Integer, edges::Vector{Vector{ntuple{2, Int}}}; weights::Vector{T} = ones(T, length(edges)))
```

は、`edges` と `weights` を持つ `dA` × `dB` 2D (ハイパー)グラフに従って、二部の `dA` × `dB` グリッド状態を生成します。

参考文献:

  * Lockhart et al., [arXiv:1705.09261](http://arxiv.org/abs/1705.09261)
  * Ghimire et al., [arXiv:2207.09826](https://arxiv.org/abs/2207.09826)
