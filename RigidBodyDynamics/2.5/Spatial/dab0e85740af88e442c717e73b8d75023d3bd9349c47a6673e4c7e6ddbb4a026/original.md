```julia
struct Wrench{T}
```

A wrench represents a system of forces.

The wrench $w^i$ expressed in frame $i$ is defined as

$$
w^{i} =
\left(\begin{array}{c}
\tau^{i}\\
f^{i}
\end{array}\right) =
\sum_{j}\left(\begin{array}{c}
r_{j}^{i}\times f_{j}^{i}\\
f_{j}^{i}
\end{array}\right)
$$

where the $f_{j}^{i}$ are forces expressed in frame $i$, exerted at positions $r_{j}^{i}$. $\tau^i$ is the total torque and $f^i$ is the total force.
