```
genus(L::HermLat) -> HermGenus
```

Return the global genus symbol `G` of the hermitian lattice `L`. `G` satisfies:

  * its local genus symbols correspond to those of the completions of `L` at the bad prime ideals of `L`, i.e. the prime ideals dividing either the scale of `L`, or the volume of `L`, or the discriminant of $\mathcal O_E$, and also the dyadic prime ideals of $\mathcal O_K$;
  * signatures are those of the Gram matrix of the rational span of `L`. They are given at the real infinite places of `K` which split into complex places of `E`.
