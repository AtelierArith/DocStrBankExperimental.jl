```
change_coefficient_ring(R::Ring, L::ModAlgAssLat{ZZRing}) -> ModAlgAss
```

Given a lattice $L$ over an $\mathbf{Z}$-order $L$, return the $L \otimes R$ over the ring $R$.

Note that the module will be defined without algebra and the action will be given by $\rank(O)$ many generators.
