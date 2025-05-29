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

  * `d::DeterministicSamples`: 親分布からのサンプル
  * `ϵ::Float64`: サンプル分布からのワッサースタイン距離（0より大きくなければならない）。 (デフォルト: 0.01)
  * `Λ::Float64`: サンプル値の周りの不確実性（0より大きくなければならない）。 (デフォルト: maximum(d))

References:

  * NingNingによるワッサースタインDROに関する論文（補題1-3）： https://ieeexplore.ieee.org/abstract/document/9311154
