```
log(G::SpecialEuclidean, g)
log!(G::SpecialEuclidean, X, g)
```

Compute the Lie group logarithm function on the [`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(3)$, where `e` is the [`Identity`](@ref) on $\mathrm{SE}(3)$ `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{3}}` for dispatch.

Since $g=(R,t) ∈ \mathrm{SE}(3)$ consists of a rotation component $R ∈ \mathrm{SO}(3)$ and a translation component $t ∈ \mathcal T(2)$, we first compute $Y = \log_{\mathrm{SO}(3)}R$. Then we can use [`vee`](@ref) on $\mathrm{SO}(3)$ to obtain the angle of rotation $α$ (or alternatively using $\sqrt{2}α = \lVert Y \rVert_{}$)

For $α ≠ 0$ define

$$
V_α = I_3 - \frac{1}{2}Y + β Y^2, \quad\text{ where } β = \frac{1}{α^2} - \frac{1 + \cos(α)}{2α\sin(α)}
$$

and $V_0 = I_3$, where $I_3$ is the identity matrix. Note that this is the inverse of $U_α$ as given in the group exponential

Then the result $X = (Y, v) ∈ \mathfrak se(3)$ is given by $Y ∈ \mathfrak so(3)$ as computed above and $v = V_α t ∈ \mathfrak t(3)$.

This result can be computed in-place of `X`.
