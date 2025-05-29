```
NonReversibleSwap <: AbstractSwapStrategy
```

At every swap step taken, this strategy *deterministically* traverses first the odd chain indices, proposing swaps between neighbors, and then in the *next* swap step taken traverses even chain indices, proposing swaps between neighbors.

See [^SYED19] for more on this approach, referred to as DEO in their paper.

[^SYED19]: Syed, S., Bouchard-Côté, Alexandre, Deligiannidis, G., & Doucet, A., Non-reversible Parallel Tempering: A Scalable Highly Parallel MCMC Scheme, arXiv:1905.02939,  (2019).
