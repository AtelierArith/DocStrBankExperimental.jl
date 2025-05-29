```
MatrixTDist(ν, M, Σ, Ω)
```

```julia
ν::Real            positive degrees of freedom
M::AbstractMatrix  n x p location
Σ::AbstractPDMat   n x n scale
Ω::AbstractPDMat   p x p scale
```

The [matrix *t*-distribution](https://en.wikipedia.org/wiki/Matrix_t-distribution) generalizes the multivariate *t*-distribution to $n\times p$ real matrices $\mathbf{X}$. If $\mathbf{X}\sim \textrm{MT}_{n,p}(\nu,\mathbf{M},\boldsymbol{\Sigma}, \boldsymbol{\Omega})$, then its probability density function is

$$
f(\mathbf{X} ; \nu,\mathbf{M},\boldsymbol{\Sigma}, \boldsymbol{\Omega}) =
c_0 \left|\mathbf{I}_n + \boldsymbol{\Sigma}^{-1}(\mathbf{X} - \mathbf{M})\boldsymbol{\Omega}^{-1}(\mathbf{X}-\mathbf{M})^{\rm{T}}\right|^{-\frac{\nu+n+p-1}{2}},
$$

where

$$
c_0=\frac{\Gamma_p\left(\frac{\nu+n+p-1}{2}\right)}{(\pi)^\frac{np}{2} \Gamma_p\left(\frac{\nu+p-1}{2}\right)} |\boldsymbol{\Omega}|^{-\frac{n}{2}} |\boldsymbol{\Sigma}|^{-\frac{p}{2}}.
$$

If the joint distribution $p(\mathbf{S},\mathbf{X})=p(\mathbf{S})p(\mathbf{X}|\mathbf{S})$ is given by

$$
\begin{aligned}
\mathbf{S}&\sim \textrm{IW}_n(\nu + n - 1, \boldsymbol{\Sigma})\\
\mathbf{X}|\mathbf{S}&\sim \textrm{MN}_{n,p}(\mathbf{M}, \mathbf{S}, \boldsymbol{\Omega}),
\end{aligned}
$$

then the marginal distribution of $\mathbf{X}$ is $\textrm{MT}_{n,p}(\nu,\mathbf{M},\boldsymbol{\Sigma},\boldsymbol{\Omega})$.
