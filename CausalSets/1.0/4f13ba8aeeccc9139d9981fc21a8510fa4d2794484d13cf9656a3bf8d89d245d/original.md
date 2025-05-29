```
HypercylinderManifold{N}(α::Float64) <: ConformallyHypercylindericalManifold{N}
```

The manifold $\mathbb{R} \times S^{N-1}$, where $S^{N-1}$ is the $N-1$-sphere. The parameter `α` is the scaling factor of this manifold relative to the unit hypercylinder.

The coordinate tuple is $(t, θ_1, \cdots, θ_{N-1})$, where the $θ_i$ are standard spherical coordinates defined by the following embedding of $S^{N-1}$ into $\mathbb{R}^N$:

$$
\begin{aligned}
x_1 &= \cos(θ_1) \\
x_2 &= \sin(θ_1) \cos(θ_2) \\
x_3 &= \sin(θ_1) \sin(θ_2) \cos(θ_3) \\
&\vdots \\
x_{N-1} &= \sin(θ_1) \cdots \sin(θ_{N-2}) \cos(θ_{N-1}) \\
x_N &= \sin(θ_1) \cdots \sin(θ_{N-2}) \sin(θ_{N-1})
\end{aligned}
$$

The angles $θ_1$ to $θ_{N-2}$ are in $[0, \pi]$, and $θ_{N-1}$ is in $[0, 2\pi)$.

The metric is:

$$
\begin{aligned}
\mathrm{d} s^2 = - \alpha^2 \left( - \mathrm{d} t^2 + \mathrm{d} Ω_{N-1}^2 \right)
\end{aligned}
$$

where $\mathrm{d} Ω_{N-1}^2$ is the standard line element on the $N - 1$-sphere.
