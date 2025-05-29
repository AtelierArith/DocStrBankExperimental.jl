```
MomentUncertainty <: CenteredAmbiguitySet
```

$$
\left\{ r  \; \middle| \begin{array}{ll}
s.t.  \quad (\mathbb{E} [r] - \hat{r}) ' \Sigma^{-1} (\mathbb{E} [r] - \hat{r}) \leq \gamma_1 \\
\quad \quad \mathbb{E} [ (r - \hat{r}) ' (r - \hat{r}) ] \leq \gamma_2 \Sigma \\
\end{array}
\right\} \\
$$

属性:

  * `d::Sampleable{Multivariate, Continous}`: 不確実な平均を持つ親分布
  * `γ1::Float64`: 平均周りの均一な不確実性（0より大きくなければならない）。
  * `γ2::Float64`: 共分散周りの不確実性（1より大きくなければならない）。

参考文献:

  * Delageのモーメント不確実性に関する論文: https://www.researchgate.net/publication/220244490*Distributionally*Robust*Optimization*Under*Moment*Uncertainty*with*Application*to*Data-Driven_Problems
