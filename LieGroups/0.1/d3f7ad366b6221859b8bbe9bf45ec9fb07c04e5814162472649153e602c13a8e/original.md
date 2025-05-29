```
exp(G::SpecialEuclidean, X)
exp!(G::SpecialEuclidean, g, X)
```

Compute the Lie group exponential function on the [`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(3)$ using a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{3}}` for dispatch.

Since $X = (Y, v) ∈ \mathfrak se(3)$ consists of a rotation component $Y ∈ \mathfrak se(3)$ and a translation component $v ∈ \mathfrak t(3)$, we can use [`vee`](@ref) on $\mathrm{SO}(3)$ computing the coefficients norm to obtain the angle of rotation $α$ (or alternatively using $\sqrt{2}α = \lVert Y \rVert_{}$).

For $α ≠ 0$ define

$$
U_α = I_3 + \frac{1-\cosα}{α^2}Y + \frac{α-\sinα}{α^3}Y^2,
$$

and $U_0 = I_3$, where $I_2$ is the identity matrix.

Then the result $g=(R,t)$ is given by

$$
R = \exp_{\mathrm{SO}(3)}Y ∈ \mathrm{SO}(3),
\quad
\text{ and }
\quad
t = U_αv ∈ \mathcal T(3).
$$

This result can be computed in-place of `g`.
