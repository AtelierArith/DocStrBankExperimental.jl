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

Atributes:

  * `d::Sampleable{Multivariate, Continous}`: The parent distribution with an uncertain mean
  * `γ1::Float64`: Uniform uncertainty around the mean (has to be greater than 0).
  * `γ2::Float64`: Uncertainty around the covariance (has to be greater than 1).

References:

  * Delage paper on moment uncertainty: https://www.researchgate.net/publication/220244490*Distributionally*Robust*Optimization*Under*Moment*Uncertainty*with*Application*to*Data-Driven_Problems
