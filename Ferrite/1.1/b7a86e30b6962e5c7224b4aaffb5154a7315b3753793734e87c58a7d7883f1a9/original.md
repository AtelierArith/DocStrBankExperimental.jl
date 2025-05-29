```
ProjectedDirichlet(field_name::Symbol, facets::AbstractSet{FacetIndex}, f::Function; qr_order = -1)
```

A `ProjectedDirichlet` condition enforces conditions for `field_name` on the boundary, `facets`, for non-nodal interpolations (e.g. $H(\mathrm{div})$ or $H(\mathrm{curl})$) by minimizing the L2 error between the function `f(x, t, n)` and the values described by the FE approximation on the facet, $\Gamma^f$. The arguments to the function are the coordinate, $\boldsymbol{x}$, the time, $t$, and the facet normal, $\boldsymbol{n}$. The quadrature rule is automatically created, but the default order, `qr_order = 2 * ip_order` (may be refined in future releases), where `ip_order` is the order of the interpolation, can be overrided if desired.

# H(div) interpolations

For H(div), we want to prescribe the normal flux, $q_\mathrm{n} = f(\boldsymbol{x}, t, \boldsymbol{n})$. To that end, we want to find the degree of freedom values, $a_j^f$, associated with the facet that minimizes

$$
U(\boldsymbol{q}(\boldsymbol{x})) = \int_{\Gamma^f}
\left[\boldsymbol{q}(\boldsymbol{x}) \cdot \boldsymbol{n} - f(\boldsymbol{x}, t, \boldsymbol{n}) \right]^2 \mathrm{d}\Gamma
$$

with $\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_j(\boldsymbol{x}) a_j^f$. Finding the stationary point by taking the directional derivative in all possible directions, $\delta\boldsymbol{q}(\boldsymbol{x})$, yields,

$$
0 = \lim_{\epsilon\rightarrow 0}\frac{\partial}{\partial \epsilon}
U\big(\boldsymbol{q}(\boldsymbol{x}) + \epsilon \delta\boldsymbol{q}(\boldsymbol{x})\big)
 = 2\int_{\Gamma^f} \left[\boldsymbol{q}(\boldsymbol{x}) \cdot \boldsymbol{n} - f(\boldsymbol{x}, t, \boldsymbol{n})\right]
    \delta\boldsymbol{q}(\boldsymbol{x}) \cdot \boldsymbol{n}\ \mathrm{d}\Gamma
$$

Inserting the FE-approximations, $\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_j(\boldsymbol{x}) a_j^f$ and $\delta\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_i(\boldsymbol{x}) c_i^f$, and using the arbitrariness of $c_i^f$, yields the linear equation system,

$$
\underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \cdot \boldsymbol{n}^f\right]\left[\boldsymbol{N}^f_j \cdot \boldsymbol{n}^f\right]\ \mathrm{d}\Gamma}_{K^f_{ij}}\ a_j^f
= \underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \cdot \boldsymbol{n}^f\right] f(\boldsymbol{x}, t, \boldsymbol{n})\ \mathrm{d}\Gamma}_{f^f_i}
$$

determining the coefficients to be prescribed, $a_j^f$.

# H(curl) interpolations

For H(curl), we want to prescribe the tangential flux, $\boldsymbol{q}_\mathrm{t} = \boldsymbol{f}(\boldsymbol{x}, t, \boldsymbol{n})$. To that end, we want to find the degree of freedom values, $a_j^f$, associated with the the facet that minimizes

$$
U(\boldsymbol{q}(\boldsymbol{x})) = \int_{\Gamma^f}
\left\vert\left\vert
    \boldsymbol{q}(\boldsymbol{x}) \times \boldsymbol{n} - \boldsymbol{f}(\boldsymbol{x}, t, \boldsymbol{n})
\right\vert\right\vert^2
\mathrm{d}\Gamma
$$

with $\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_j(\boldsymbol{x}) a_j^f$. Similar to for $H(\mathrm{div})$, we find the minimum by setting the directional derivative equal to zero, which after inserting the FE-approximations yields the linear equation system,

$$
\underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \times \boldsymbol{n}^f\right]\cdot\left[\boldsymbol{N}^f_j \times \boldsymbol{n}^f\right]\ \mathrm{d}\Gamma}_{K^f_{ij}}\ a_j^f
= \underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \times \boldsymbol{n}^f\right]\cdot \boldsymbol{f}(\boldsymbol{x}, t, \boldsymbol{n})\ \mathrm{d}\Gamma}_{f^f_i}
$$

determining the coefficients to be prescribed, $a_j^f$
