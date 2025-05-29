```
log(G::SpecialEuclidean, g)
log!(G::SpecialEuclidean, X, g)
```

Compute the Lie group logarithm function on the [`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(2)$, and `G` uses a [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{2}}` for dispatch.

Since $g=(R,t) ∈ \mathrm{SE}(2)$ consists of a rotation component $R ∈ \mathrm{SO}(2)$ and a translation component $t ∈ \mathcal T(2)$, we first compute $Y = \log_{\mathrm{SO}(2)}R$. Then we can use [`vee`](@ref) on $\mathrm{SO}(2)$ to obtain the angle of rotation $α$ (or alternatively using $\sqrt{2}α = \lVert Y \rVert_{}$)

For $α ≠ 0$ define

$$
V_α = \frac{α}{2} \begin{pmatrix} \frac{\sinα}{1-\cosα} & 1\\ -1 & \frac{\sinα}{1-\cosα}\end{pmatrix}
$$

and $V_0 = I_2$, where $I_2$ is the identity matrix. Note that this is the inverse of $U_α$ as given in the group exponential

Then the result $X = (Y, v) ∈ \mathfrak se(2)$ is given by $Y ∈ \mathfrak so(2)$ as computed above and

$$
v = V_αr ∈ \mathcal T(2),
$$

where $v$ is computed in-place without setting up $V_α$

This result can be computed in-place of `g`.
