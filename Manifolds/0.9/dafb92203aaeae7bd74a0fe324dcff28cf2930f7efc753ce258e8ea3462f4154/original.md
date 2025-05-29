```
project(M::EssentialManifold, p, X)
```

Project the matrix `X` onto the tangent space

$$
T_{p} \text{SO}(3)^2 = T_{\text{vp}}\text{SO}(3)^2 ⊕ T_{\text{hp}}\text{SO}(3)^2,
$$

by first computing its projection onto the vertical space $T_{\text{vp}}\text{SO}(3)^2$ using [`vert_proj`](@ref). Then the orthogonal projection of `X` onto the horizontal space $T_{\text{hp}}\text{SO}(3)^2$ is defined as

$$
\Pi_h(X) = X - \frac{\text{vert\_proj}_p(X)}{2} \begin{bmatrix} R_1^T e_z \\ R_2^T e_z \end{bmatrix},
$$

with $R_i = R_0 R'_i, i=1,2,$ where $R'_i$ is part of the pose of camera $i$ $g_i = (R'_i,T'_i) ∈ \text{SE}(3)$ and $R_0 ∈ \text{SO}(3)$ such that $R_0(T'_2-T'_1) = e_z$.
