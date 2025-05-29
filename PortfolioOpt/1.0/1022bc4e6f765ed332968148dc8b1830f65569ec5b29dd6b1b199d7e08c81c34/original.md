```
DuWassersteinBall <: CenteredAmbiguitySet
```

$$
\left\{ r  \; \middle| \begin{array}{ll}
s.t.  \quad d_w(P, \hat{P}_N) \leq \epsilon \\
\quad \quad || \xi || \leq \Lambda \\
\quad \quad [\xi; 0] + [0_{m x 1}; \Lambda] \in K \\
\quad \quad K = {[\omega, \pi] \in R^m x R: \pi \geq ||\omega||^*} \\
\end{array}
\right\} \\
$$

Atributes:

  * `d::DeterministicSamples`: Samples from the parent distribution
  * `ϵ::Float64`: Wasserstein distance from sampled distribution (has to be greater than 0). (default: 0.01)
  * `Λ::Float64`: Uncertainty around sampled values (has to be greater than 0). (default: maximum(d))

References:

  * NingNing paper on Wasserstein DRO (Corollary 1-3): https://ieeexplore.ieee.org/abstract/document/9311154
