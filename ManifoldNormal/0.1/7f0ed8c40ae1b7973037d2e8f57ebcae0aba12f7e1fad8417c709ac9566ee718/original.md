```
scaled_distance(D::ActionDistribution, x)
```

Start with a `ActionDistribution(μ,Σ)` distribution with mean $μ$ lying on the sample manifold $M$, and covariance $Σ$ in the Lie algebra $\mathfrak{g}$ of the group $G$. The infinitesimal action of the group $G$ on the manifold $M$ gives rise to the linear map $P \colon \mathfrak{g} \to T_{μ}M$, which in turns gives the projected covariance $PΣP^*$ on the tangent space $T_{μ}M$.

One then measures the scaled distance from $μ$ to $x$ from $v := \log(μ, x)$ with the formula

$$
\frac{\sqrt{v^T (PΣP^*)^{-1} v}}{\sqrt{n}}
$$

(where $v$ is regarded as a column matrix here) and $n$ is the dimension of the sample manifold $M$.
