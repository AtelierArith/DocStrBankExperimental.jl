```
DeSitterManifold{N}(α::Float64) <: ConformallyHypercylindricalManifold{N}
```

De Sitter Manifold with one time coordinate and $N - 1$ spatial coordinates. The parameter `α` is the scaling factor relative to the hyperboloid embedding. The coordinate $N$-tuple is $(η, θ_i)$, where $η$ is the conformal time, and the $θ_i$ are the $N - 1$ spherical angles parametrizing a spacelike slice of the de Sitter manifold. The $N - 1$-sphere coordinate system is the same as in the case of [`HypercylinderManifold`](@ref).

This manifold can be defined as the submanifold of $1 + N$-dimensional Minkowski spacetime satisfying $x_μ x^μ = α^2$. This is the hyperboloid of one sheet parametrized by the angles $(ξ, θ_i)$:

$$
\begin{aligned}
x_0 &= α \sinh(ξ) \\
x_i &= α \cosh(ξ) X_i
\end{aligned}
$$

where $X_i, 1 \leq i \leq N$ are the unit $N$-sphere coordinates corresponding to the spherical angles $θ_i, 1 \leq i \leq N - 1$. The induced metric of this coordinate system is:

$$
\begin{aligned}
\mathrm{d} s^2  = - α^2 (\mathrm{d} ξ^2 + \cosh^2(ξ) \mathrm{d} Ω_{N-1}^2)
\end{aligned}
$$

where $\mathrm{d} Ω_{N-1}^2$ is the standard line element on the $N - 1$-sphere.

We can now reparametrize the time coordinate to the *conformal time* $η$:

$$
\begin{aligned}
\cosh(ξ) = \frac{1}{\cos(η)}
\end{aligned}
$$

such that the metric becomes conformally equivalent to the hypercylinder metric:

$$
\begin{aligned}
\mathrm{d} s^2  = \frac{α^2}{\cos^2(η)} \left( - \mathrm{d} ξ^2 + \mathrm{d} Ω_{N-1}^2 \right)
\end{aligned}
$$

The conformal time $η$ ranges from $-π/2$ to $π/2$.
