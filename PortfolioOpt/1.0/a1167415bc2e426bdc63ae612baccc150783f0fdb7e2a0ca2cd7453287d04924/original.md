```
EllipticalSet <: CenteredAmbiguitySet{T,D}
```

$$
\left\{ \mu \; \middle| \begin{array}{ll}
s.t.  \quad \sqrt{(\hat{r} - \mu) ' \Sigma^{-1} (\hat{r} - \mu)} \leq \delta \\
\end{array}
\right\} \\
$$

Atributes:

  * `d::Sampleable{Multivariate, Continous}`: The parent distribution with an uncertain mean
  * `Δ::Array{Float64,1}`: Uniform uncertainty around mean. (default: 0.025)

References:

  * Ben-Tal, A. e Nemirovski, A. (2000). Robust solutions of linear programming problems contaminated with uncertain data. Mathematical programming, 88(3):411–424.
