```
siegel_reduction(tau::AcbMatrix) -> AcbMatrix
```

Compute the Siegel reduction of the period matrix tau, i.e. writing siegel*reduction(tau) = X +iY. We will have |X*mn| <= 1/2 for all n, m and the shortest vector of the lattice generated by Y will have squared length smaller than sqrt(3)/2.
