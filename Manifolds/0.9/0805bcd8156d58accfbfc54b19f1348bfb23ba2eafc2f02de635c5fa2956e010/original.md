```
q = exp(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},CanonicalMetric}, p, X)
exp!(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},CanonicalMetric}, q, p, X)
```

Compute the exponential map on the [`Stiefel`](@ref)`(n, k)` manifold with respect to the [`CanonicalMetric`](@ref).

First, decompose The tangent vector $X$ into its horizontal and vertical component with respect to $p$, i.e.

$$
X = pp^{\mathrm{T}}X + (I_n-pp^{\mathrm{T}})X,
$$

where $I_n$ is the $n×n$ identity matrix. We introduce $A=p^{\mathrm{T}}X$ and $QR = (I_n-pp^{\mathrm{T}})X$ the `qr` decomposition of the vertical component. Then using the matrix exponential $\operatorname{Exp}$ we introduce $B$ and $C$ as

$$
\begin{pmatrix}
B\\C
\end{pmatrix}
\coloneqq
\operatorname{Exp}\left(
\begin{pmatrix}
A & -R^{\mathrm{T}}\\ R & 0
\end{pmatrix}
\right)
\begin{pmatrix}I_k\\0\end{pmatrix}
$$

the exponential map reads

$$
q = \exp_p X = pC + QB.
$$

For more details, see [EdelmanAriasSmith:1998](@cite)[Zimmermann:2017](@cite).
