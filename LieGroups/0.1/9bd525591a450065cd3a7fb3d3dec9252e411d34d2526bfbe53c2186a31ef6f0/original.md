```
exp(G::SpecialEuclidean, X)
exp!(G::SpecialEuclidean, g, X)
```

Compute the Lie group exponential function on the [`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(2)$ using a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{2}}` for dispatch.

The Lie algebra vector $X = (Y, v) ∈ \mathfrak se(2)$ consists of a rotation component $Y ∈ \mathfrak so(2)$ and a translation component $v ∈ \mathfrak t(2)$, so we can use [`vee`](@ref) on $\mathrm{SO}(2)$ to obtain the angle of rotation $α$ (or alternatively using $\sqrt{2}α = \lVert Y \rVert_{}$)

For $α ≠ 0$ define

$$
U_α = \frac{\sinα}{α}I_2 + \frac{1-\cosα}{α^2}Y,
$$

and $U_0 = I_2$, where $I_2$ is the identity matrix.

Then the result $g=(R,t)$ is given by

$$
R = \exp_{\mathrm{SO}(2)}Y ∈ \mathrm{SO}(2),
\quad
\text{ and }
\quad
t = U_αv ∈ \mathcal T(2).
$$

This result can be computed in-place of `g`.
