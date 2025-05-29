```
is_maximal(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Bool, AbstractLat
```

Given a lattice `L` and a prime ideal `p` in the fixed ring $\mathcal O_K$ of `L` such that the norm of $L_p$ is integral, return whether `L` is maximal integral at `p`.

If `L` is locally maximal at `p`, the second output is `L`, otherwise it is a lattice `M` in the same ambient space of `L` whose completion at `p` has integral norm and is a proper overlattice of $L_p$.
