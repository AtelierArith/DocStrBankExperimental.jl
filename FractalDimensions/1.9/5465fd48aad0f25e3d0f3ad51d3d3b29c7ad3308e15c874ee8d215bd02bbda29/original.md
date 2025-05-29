```
estimate_r0_buenoorovio(X::AbstractStateSpaceSet, P = 2) → r0, ε0
```

Estimate a reasonable size for boxing `X`, proposed by Bueno-Orovio and Pérez-García [BuenoOrovio2007](@cite), before calculating the correlation dimension as presented by [Theiler1987](@cite). Return the size `r0` and the minimum interpoint distance `ε0` in the data.

If instead of boxes, prisms are chosen everything stays the same but `P` is the dimension of the prism. To do so the dimension `ν` is estimated by running the algorithm by Grassberger and Procaccia [Grassberger1983](@cite) with `√N` points where `N` is the number of total data points. An effective size `ℓ` of the attractor is calculated by boxing a small subset of size `N/10` into boxes of sidelength `r_ℓ` and counting the number of filled boxes `η_ℓ`.

$$
\ell = r_\ell \eta_\ell ^{1/\nu}
$$

The optimal number of filled boxes `η_opt` is calculated by minimising the number of calculations.

$$
\eta_\textrm{opt} = N^{2/3}\cdot \frac{3^\nu - 1}{3^P - 1}^{1/2}.
$$

`P` is the dimension of the data or the number of edges on the prism that don't span the whole dataset.

Then the optimal boxsize $r_0$ computes as

$$
r_0 = \ell / \eta_\textrm{opt}^{1/\nu}.
$$
