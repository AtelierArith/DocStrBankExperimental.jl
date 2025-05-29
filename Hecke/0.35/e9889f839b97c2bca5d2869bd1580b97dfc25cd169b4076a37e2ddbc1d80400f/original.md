```
maximal_integral_lattice(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbstractLat
```

Given a lattice `L` and a prime ideal `p` of the fixed ring $\mathcal O_K$ of `L` such that the norm of $L_p$ is integral, return a lattice `M` in the ambient space of `L` which is maximal integral at `p` and which agrees with `L` locally at all the places different from `p`.
