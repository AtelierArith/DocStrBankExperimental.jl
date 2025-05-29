```
is_maximal_integral(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Bool, AbstractLat
```

Given a lattice `L` and a prime ideal `p` of the fixed ring $\mathcal O_K$ of `L`, return whether the completion of `L` at `p` has integral norm and that `L` has no proper overlattice satisfying this property.

If the norm of `L` is not integral at `p`, the second output is `L` by default. Otherwise, either `L` is maximal at `p` and the second output is `L`, or the second output is a lattice `M` in the ambient space of `L` whose completion at `p` is a minimal overlattice of $L_p$ with integral norm.
