```
BudgetSet{T<:Real, D<:ContinuousMultivariateSampleable} <: CenteredAmbiguitySet{T,D}
```

Bertsimas's uncertainty set:

$$
\left\{ \mu \; \middle| \begin{array}{ll}
s.t.  \quad \mu_i \leq \hat{r}_i + z_i \Delta_i \quad \forall i = 1:\mathcal{N} \\
\quad \quad \mu_i \geq \hat{r}_i - z_i \Delta_i  \quad \forall i = 1:\mathcal{N} \\
\quad \quad z_i \geq 0 \quad \forall i = 1:\mathcal{N} \\
\quad \quad z_i \leq 1 \quad \forall i = 1:\mathcal{N} \\
\quad \quad \sum_{i}^{\mathcal{N}} z_i \leq \Gamma \\
\end{array}
\right\} \\
$$

Attributes:

  * `d::Sampleable{Multivariate, Continous}`: The parent distribution with an uncertain mean
  * `Δ::Array{Float64,1}`: Uncertainty around mean. (default: std(d) / 5)
  * `Γ::Float64`: Number of assets in worst case. (default: 0.1 * length(d))

References:

  * Bertsimas, D. e Sim, M. (2004). The price of robustness. Operations research, 52(1):35–53.
