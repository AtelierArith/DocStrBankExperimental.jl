```
jordan_decomposition(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem})
                            -> Vector{MatElem}, Vector{MatElem}, Vector{Int}
```

Return a Jordan decomposition of the completion of the lattice `L` at a prime ideal `p`.

The returned value consists of three lists $(M_i)_i$, $(G_i)_i$ and $(s_i)_i$ of the same length $r$. The completions of the row spans of the matrices $M_i$ yield a Jordan decomposition of $L_{p}$ into modular sublattices $L_i$ with Gram matrices $G_i$ and scale of $p$-adic valuation $s_i$.
