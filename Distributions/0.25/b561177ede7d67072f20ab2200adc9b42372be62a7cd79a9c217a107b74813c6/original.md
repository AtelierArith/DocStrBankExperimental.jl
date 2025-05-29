```
InverseWishart(ν, Ψ)
```

```julia
ν::Real           degrees of freedom (greater than p - 1)
Ψ::AbstractPDMat  p x p scale matrix
```

The [inverse Wishart distribution](http://en.wikipedia.org/wiki/Inverse-Wishart_distribution) generalizes the inverse gamma distribution to $p\times p$ real, positive definite matrices $\boldsymbol{\Sigma}$. If $\boldsymbol{\Sigma}\sim \textrm{IW}_p(\nu,\boldsymbol{\Psi})$, then its probability density function is

$$
f(\boldsymbol{\Sigma}; \nu,\boldsymbol{\Psi}) =
\frac{\left|\boldsymbol{\Psi}\right|^{\nu/2}}{2^{\nu p/2}\Gamma_p(\frac{\nu}{2})} \left|\boldsymbol{\Sigma}\right|^{-(\nu+p+1)/2} e^{-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1})}.
$$

$\mathbf{H}\sim \textrm{W}_p(\nu, \mathbf{S})$ if and only if $\mathbf{H}^{-1}\sim \textrm{IW}_p(\nu, \mathbf{S}^{-1})$.
