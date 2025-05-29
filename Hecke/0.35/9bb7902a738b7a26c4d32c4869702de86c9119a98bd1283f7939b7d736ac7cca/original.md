```
locally_isometric_sublattice(M::HermLat, L::HermLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> HermLat
```

Given rationally isometric hermitian lattices `M` and `L` over $E/K$ and a prime ideal `p` of $\mathcal O_K$, return a sublattice `N` of `M` with $N_q = M_q$ for $q \neq p$ and $N_p$ isometric to $L_p$.
