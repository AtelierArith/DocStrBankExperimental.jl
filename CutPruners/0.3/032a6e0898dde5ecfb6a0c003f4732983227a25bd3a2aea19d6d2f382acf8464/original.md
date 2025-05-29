```
DeMatosPruningAlgo <: AbstractCutPruningAlgo
```

Removes the cuts with lower trust where the trust is the number of points `x` associated to the cuts. The more points are associated, the higher is the trust.

We refer to [1] for further details.

[1] De Matos, Vitor L., Andy B. Philpott, and Erlon C. Finardi. "Improving the performance of stochastic dual dynamic programming." Journal of Computational and Applied Mathematics 290 (2015): 196-208.
