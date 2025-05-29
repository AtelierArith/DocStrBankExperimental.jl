```
Wishart(ν, S)
```

```julia
ν::Real           degrees of freedom (whole number or a real number greater than p - 1)
S::AbstractPDMat  p x p scale matrix
```

The [Wishart distribution](http://en.wikipedia.org/wiki/Wishart_distribution) generalizes the gamma distribution to $p\times p$ real, positive semidefinite matrices $\mathbf{H}$.

If $\nu>p-1$, then $\mathbf{H}\sim \textrm{W}_p(\nu, \mathbf{S})$ has rank $p$ and its probability density function is

$$
f(\mathbf{H};\nu,\mathbf{S}) = \frac{1}{2^{\nu p/2} \left|\mathbf{S}\right|^{\nu/2} \Gamma_p\left(\frac {\nu}{2}\right ) }{\left|\mathbf{H}\right|}^{(\nu-p-1)/2} e^{-(1/2)\operatorname{tr}(\mathbf{S}^{-1}\mathbf{H})}.
$$

If $\nu\leq p-1$, then $\mathbf{H}$ is rank $\nu$ and it has a density with respect to a suitably chosen volume element on the space of positive semidefinite matrices. See [here](https://doi.org/10.1214/aos/1176325375).

For integer $\nu$, a random matrix given by

$$
\mathbf{H} = \mathbf{X}\mathbf{X}^{\rm{T}},
\quad\mathbf{X} \sim \textrm{MN}_{p,\nu}(\mathbf{0}, \mathbf{S}, \mathbf{I}_{\nu})
$$

has $\mathbf{H}\sim \textrm{W}_p(\nu, \mathbf{S})$. For non-integer $\nu$, Wishart matrices can be generated via the [Bartlett decomposition](https://en.wikipedia.org/wiki/Wishart_distribution#Bartlett_decomposition).
