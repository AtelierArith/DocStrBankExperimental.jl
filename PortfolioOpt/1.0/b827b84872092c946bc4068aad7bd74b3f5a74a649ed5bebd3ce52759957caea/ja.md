```
BudgetSet{T<:Real, D<:ContinuousMultivariateSampleable} <: CenteredAmbiguitySet{T,D}
```

Bertsimasの不確実性セット：

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

属性：

  * `d::Sampleable{Multivariate, Continous}`: 不確実な平均を持つ親分布
  * `Δ::Array{Float64,1}`: 平均周辺の不確実性。（デフォルト: std(d) / 5）
  * `Γ::Float64`: 最悪の場合の資産数。（デフォルト: 0.1 * length(d)）

参考文献：

  * Bertsimas, D. e Sim, M. (2004). The price of robustness. Operations research, 52(1):35–53.
