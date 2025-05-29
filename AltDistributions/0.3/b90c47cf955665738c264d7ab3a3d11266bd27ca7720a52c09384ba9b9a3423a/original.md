```julia
LKJL(η)

```

The LKJ distribution (Lewandowski et al 2009) for the Cholesky factor L of correlation matrices.

A correlation matrix $Ω=LL'$ has the density $|Ω|^{η-1}$. However, it is usually not necessary to construct $Ω$, so this distribution is formulated for the Cholesky decomposition `L*L'`, and takes `L` directly.

Note that the methods **does not check if `L` yields a valid correlation matrix**.

Valid values are $η > 0$. When $η > 1$, the distribution is unimodal at `Ω=I`, while $0 < η < 1$ has a trough. $η = 2$ is recommended as a vague prior.

When $η = 1$, the density is uniform in `Ω`, but not in `L`, because of the Jacobian correction of the transformation.
