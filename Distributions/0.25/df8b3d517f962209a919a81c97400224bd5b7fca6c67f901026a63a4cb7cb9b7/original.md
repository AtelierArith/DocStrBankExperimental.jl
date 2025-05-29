```
MatrixFDist(n1, n2, B)
```

```julia
n1::Real          degrees of freedom (greater than p - 1)
n2::Real          degrees of freedom (greater than p - 1)
B::AbstractPDMat  p x p scale
```

The [matrix *F*-distribution](https://projecteuclid.org/euclid.ba/1515747744) (sometimes called the matrix beta type II distribution) generalizes the *F*-Distribution to $p\times p$ real, positive definite matrices $\boldsymbol{\Sigma}$. If $\boldsymbol{\Sigma}\sim \textrm{MF}_{p}(n_1/2,n_2/2,\mathbf{B})$, then its probability density function is

$$
f(\boldsymbol{\Sigma} ; n_1,n_2,\mathbf{B}) =
\frac{\Gamma_p(\frac{n_1+n_2}{2})}{\Gamma_p(\frac{n_1}{2})\Gamma_p(\frac{n_2}{2})}
|\mathbf{B}|^{n_2/2}|\boldsymbol{\Sigma}|^{(n_1-p-1)/2}|\mathbf{B}+\boldsymbol{\Sigma}|^{-(n_1+n_2)/2}.
$$

If the joint distribution $p(\boldsymbol{\Psi},\boldsymbol{\Sigma})=p(\boldsymbol{\Psi})p(\boldsymbol{\Sigma}|\boldsymbol{\Psi})$ is given by

$$
\begin{aligned}
\boldsymbol{\Psi}&\sim \textrm{W}_p(n_1, \mathbf{B})\\
\boldsymbol{\Sigma}|\boldsymbol{\Psi}&\sim \textrm{IW}_p(n_2, \boldsymbol{\Psi}),
\end{aligned}
$$

then the marginal distribution of $\boldsymbol{\Sigma}$ is $\textrm{MF}_{p}(n_1/2,n_2/2,\mathbf{B})$.
