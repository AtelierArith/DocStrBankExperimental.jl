```julia
struct SpatialInertia{T}
```

A spatial inertia, or inertia matrix, represents the mass distribution of a rigid body.

A spatial inertia expressed in frame $i$ is defined as:

$$
I^i =
\int_{B}\rho\left(x\right)\left[\begin{array}{cc}
\hat{p}^{T}\left(x\right)\hat{p}\left(x\right) & \hat{p}\left(x\right)\\
\hat{p}^{T}\left(x\right) & I
\end{array}\right]dx=\left[\begin{array}{cc}
J & \hat{c}\\
\hat{c}^{T} & mI
\end{array}\right]
$$

where $\rho(x)$ is the density of point $x$, and $p(x)$ are the coordinates of point $x$ expressed in frame $i$. $J$ is the mass moment of inertia, $m$ is the total mass, and $c$ is the 'cross part', center of mass position scaled by $m$.

!!! warning
    The `moment` field of a `SpatialInertia` is the moment of inertia **about the origin of its `frame`**, not about the center of mass.

