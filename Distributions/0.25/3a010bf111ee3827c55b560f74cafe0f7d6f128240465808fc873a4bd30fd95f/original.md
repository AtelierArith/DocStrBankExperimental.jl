```
MatrixNormal(M, U, V)
```

```julia
M::AbstractMatrix  n x p mean
U::AbstractPDMat   n x n row covariance
V::AbstractPDMat   p x p column covariance
```

The [matrix normal distribution](https://en.wikipedia.org/wiki/Matrix_normal_distribution) generalizes the multivariate normal distribution to $n\times p$ real matrices $\mathbf{X}$. If $\mathbf{X}\sim \textrm{MN}_{n,p}(\mathbf{M}, \mathbf{U}, \mathbf{V})$, then its probability density function is

$$
f(\mathbf{X};\mathbf{M}, \mathbf{U}, \mathbf{V}) = \frac{\exp\left( -\frac{1}{2} \, \mathrm{tr}\left[ \mathbf{V}^{-1} (\mathbf{X} - \mathbf{M})^{\rm{T}} \mathbf{U}^{-1} (\mathbf{X} - \mathbf{M}) \right] \right)}{(2\pi)^{np/2} |\mathbf{V}|^{n/2} |\mathbf{U}|^{p/2}}.
$$

$\mathbf{X}\sim \textrm{MN}_{n,p}(\mathbf{M},\mathbf{U},\mathbf{V})$ if and only if $\text{vec}(\mathbf{X})\sim \textrm{N}(\text{vec}(\mathbf{M}),\mathbf{V}\otimes\mathbf{U})$.
