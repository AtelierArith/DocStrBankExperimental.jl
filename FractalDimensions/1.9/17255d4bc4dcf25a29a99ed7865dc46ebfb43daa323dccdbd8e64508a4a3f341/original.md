```
Exceedances(p::Real, estimator::Symbol)
```

Instructions type for [`extremevaltheory_dims_persistences`](@ref) and related functions. This method sets a threshold and fits the exceedances to Generalized Pareto Distribution (GPD). The parameter `p` is a number between 0 and 1 that determines the p-quantile for the threshold and computation of the extremal index. The argument `estimator` is a symbol that decides how the GPD is fitted to the data. It can take the values `:exp, :pwm, :mm`, as in [`estimate_gpd_parameters`](@ref).

## Description

For each state space point $\mathbf{x}_i$ in `X` we compute $g_i = -\log(||\mathbf{x}_i - \mathbf{x}_j|| ) \; \forall j = 1, \ldots, N$ with $||\cdot||$ the Euclidean distance. Next, we choose an extreme quantile probability $p$ (e.g., 0.99) for the distribution of $g_i$. We compute $g_p$ as the $p$-th quantile of $g_i$. Then, we collect the exceedances of $g_i$, defined as $E_i = \{ g_i - g_p: g_i \ge g_p \}$, i.e., all values of $g_i$ larger or equal to $g_p$, also shifted by $g_p$. There are in total $n = N(1-q)$ values in $E_i$. According to extreme value theory, in the limit $N \to \infty$ the values $E_i$ follow a two-parameter Generalized Pareto Distribution (GPD) with parameters $\sigma,\xi$ (the third parameter $\mu$ of the GPD is zero due to the positive-definite construction of $E$). Within this extreme value theory approach, the local dimension $\Delta^{(E)}_i$ assigned to state space point $\textbf{x}_i$ is given by the inverse of the $\sigma$ parameter of the GPD fit to the data[^Lucarini2012], $\Delta^{(E)}_i = 1/\sigma$. $\sigma$ is estimated according to the `estimator` keyword.

A more precise description of this process is given in the review paper [Datseris2023](@cite).
