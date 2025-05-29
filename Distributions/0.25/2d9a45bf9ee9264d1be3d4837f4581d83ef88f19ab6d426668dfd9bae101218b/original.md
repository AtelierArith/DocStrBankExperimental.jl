```
MatrixBeta(p, n1, n2)
```

```julia
p::Int    dimension
n1::Real  degrees of freedom (greater than p - 1)
n2::Real  degrees of freedom (greater than p - 1)
```

The [matrix beta distribution](https://en.wikipedia.org/wiki/Matrix_variate_beta_distribution) generalizes the beta distribution to $p\times p$ real matrices $\mathbf{U}$ for which $\mathbf{U}$ and $\mathbf{I}_p-\mathbf{U}$ are both positive definite. If $\mathbf{U}\sim \textrm{MB}_p(n_1/2, n_2/2)$, then its probability density function is

$$
f(\mathbf{U}; n_1,n_2) = \frac{\Gamma_p(\frac{n_1+n_2}{2})}{\Gamma_p(\frac{n_1}{2})\Gamma_p(\frac{n_2}{2})}
|\mathbf{U}|^{(n_1-p-1)/2}\left|\mathbf{I}_p-\mathbf{U}\right|^{(n_2-p-1)/2}.
$$

If $\mathbf{S}_1\sim \textrm{W}_p(n_1,\mathbf{I}_p)$ and $\mathbf{S}_2\sim \textrm{W}_p(n_2,\mathbf{I}_p)$ are independent, and we use $\mathcal{L}(\cdot)$ to denote the lower Cholesky factor, then

$$
\mathbf{U}=\mathcal{L}(\mathbf{S}_1+\mathbf{S}_2)^{-1}\mathbf{S}_1\mathcal{L}(\mathbf{S}_1+\mathbf{S}_2)^{-\rm{T}}
$$

has $\mathbf{U}\sim \textrm{MB}_p(n_1/2, n_2/2)$.
