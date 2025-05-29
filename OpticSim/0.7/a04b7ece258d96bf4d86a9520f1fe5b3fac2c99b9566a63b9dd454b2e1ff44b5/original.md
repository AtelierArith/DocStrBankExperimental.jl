```
QTypeSurface{T,D,M,N} <: ParametricSurface{T,D}
```

Surface incorporating the QType polynomials - radius and conic are defined relative to absolute semi-diameter, QType terms are normalized according to the `normradius` parameter. `T` is the datatype, `D` is the dimensionality, `M` and `N` are the maximum QType terms used.

The surface is centered at the origin and treated as being the cap of an infinite cylinder, thus creating a true half-space. Outside of 0 <= ρ <= 1 the height of the surface is not necessarily well defined, so NaN may be returned.

```julia
QTypeSurface(semidiameter; radius = Inf, conic = 0.0, αcoeffs = nothing, βcoeffs = nothing, normradius = semidiameter)
```

`αcoeffs` and `βcoeffs` should be a vector of tuples of the form `(m, n, v)` where `v` is the value of the coefficient $α_n^m$ or $β_n^m$ respectively.

The sag is defined by the equation

$$
\begin{aligned}
z(r,\phi) = & \frac{cr^2}{1 + \sqrt{1 - (1+k)c^2r^2}} + \frac{\sqrt{1 + kc^2r^2}}{\sqrt{1-(1+k)c^2r^2}} \cdot \\
             & \left\{ \rho^2(1-\rho^2)\sum_{n=0}^{N}\alpha_n^0 Q_n^0 (\rho^2) + \sum_{m=1}^{M}\rho^m\sum_{n=0}^N \left[ \alpha_n^m\cos{m\phi} +\beta_n^m\sin{m\phi}\right]Q_n^m(\rho^2) \right\}
\end{aligned}
$$

where $\rho = \frac{r}{\texttt{normradius}}$, $c = \frac{1}{\texttt{radius}}$, $k = \texttt{conic}$ and $Q_n^m$ is the QType polynomial index $m$, $n$.
