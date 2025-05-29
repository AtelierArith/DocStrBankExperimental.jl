```julia
struct Momentum{T}
```

A `Momentum` is the product of a `SpatialInertia` and a `Twist`, i.e.

$$
h^i =
\left(\begin{array}{c}
k^{i}\\
l^{i}
\end{array}\right) =
I^i T^{i, j}_k
$$

where $I^i$ is the spatial inertia of a given body expressed in frame $i$, and $T^{i, j}_k$ is the twist of frame $k$ (attached to the body) with respect to inertial frame $j$, expressed in frame $i$. $k^i$ is the angular momentum and $l^i$ is the linear momentum.
