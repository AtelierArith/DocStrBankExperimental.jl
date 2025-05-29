```
offline(apt::Adapt_MZI, alg; target::Symbol=:sharpness, eps = GLOBAL_EPS, seed=1234)
```

Offline adaptive phase estimation in the MZI.

  * `apt`: Adaptive MZI struct which contains `x`, `p`, and `rho0`.
  * `alg`: The algorithms for searching the optimal tunable phase. Here, DE and PSO are available.
  * `target`: Setting the target function for calculating the tunable phase. Options are: "sharpness" and "MI".
  * `eps`: Machine epsilon.
  * `seed`: Random seed.
