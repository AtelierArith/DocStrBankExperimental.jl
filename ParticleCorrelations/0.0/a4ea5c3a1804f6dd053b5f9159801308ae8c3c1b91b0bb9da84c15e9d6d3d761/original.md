```
gls_pair_radial_fun(pair_corr_distance::Function, a12::T; polynomial_order::Int, mesh_size::Int)
```

Return a function `gls_fun`. For any radial distances `r1` and `r2` we have `gls = gls_fun(r1,r2)` where `gls` is an array of the Legendre coefficients for the pair correlation.

Using mathematics, we have that such that $g(r_1,r_2,\cos \theta_{12}) = \sum_{\ell_1 =0} \frac{2\ell_1 + 1}{4\pi} gls[\ells+1] P_{\ell_1}(\cos \theta_{12})$, where $g(r_1,r_2,\cos \theta_{12})$ is the radially symmetric pair-correlation, so it depends only on the radial distances $r_1$ and $r_2$, and the angle between two position vectors $\theta_{12}$.

The function `gls_fun` is calculated from the function `pair_corr_distance`, where `pair_corr_distance(sqrt(r1^2 + r2^2 - 2r1 * r2 * cos(θ12)))` gives the pair correlation.
