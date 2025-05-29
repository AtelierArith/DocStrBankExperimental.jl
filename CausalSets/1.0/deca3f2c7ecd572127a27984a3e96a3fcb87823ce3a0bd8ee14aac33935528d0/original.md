```
AntiDeSitterManifold{N}(α::Float64) <: ConformallyTimesliceableManifold{N}
```

Anti de Sitter manifold with one time coordinate and $N - 1$ spatial coordinates. The parameter $α$ is the scaling factor relative to the unit hyperboloid embedding. The coordinate $N$-tuple is $(η, χ, θ_i)$, where $η$ is the conformal time, $χ$ is the conformal polar angle, and the $θ_i$ are the $N - 2$ spherical angles parametrizing one shell of the spatial part of the manifold. The $N-2$-sphere coordinate system is the same as in the case of [`HypercylinderManifold`](@ref).

This manifold can be defined as the submanifold of Minkowski space with 2 temporal and $N - 1$ spatial dimensions with the condition $x_μ x^μ = - α^2$. This is the hyperboloid of one sheet parametrized by the angles $(η, ρ, θ_i)$:

$$
\begin{aligned}
x_0 &= α \sin(η) \cosh(ρ) \\
x_1 &= α \cos(η) \cosh(ρ) \\
x_i &= α \sinh(ρ) X_i
\end{aligned}
$$

where $x_1$ and $x_2$ are the two time dimensions, and the $x_i, 2 \leq i \leq N$ are the unit $N-2$-sphere coordinates corresponding to the spherical angles $θ_j, 1 \leq j \leq N-1$. The induced metric of this submanifold is:

$$
\begin{aligned}
\mathrm{d} s^2 = α^2 \left(- \cosh^2(ρ) \mathrm{d} η^2 + \mathrm{d} ρ^2 + \sinh^2(ρ) \mathrm{d} Ω_{N-2}^2\right)
\end{aligned}
$$

where $\mathrm{d} Ω_{N-2}^2$ is the standard line element of the $N-2$-sphere. 

In principle, this manifold would contain closed timelike curves - the ones we get when we go around the circle in the $x_0, x_1$ timelike slice one time. This would make this manifold unsuitable for causal set theory. Therefore, we unroll the embedding and let $ρ$ have values in the entirety of $\mathbb{R}$ instead of just $[0, 2π)$.

We can now reparametrize the hyperbolic polar angle $ρ$ to the *conformal polar angle* $χ$ with:

$$
\begin{aligned}
\cosh(ρ) = \frac{1}{\cos(χ)}
\end{aligned}
$$

Then, the metric becomes conformally flat with hyperspherical coordinates for the spacelike slices:

$$
\begin{aligned}
\mathrm{d} s^2 = \frac{α^2}{\cos^2(χ)} \left( - \mathrm{d} η^2 + \mathrm{d} χ^2 + \sin^2(χ) \mathrm{d} Ω_{N-2}^2 \right)
\end{aligned}
$$

Unlike a normal polar angle, the conformal polar angle $χ$ only ranges from $0$ to $π/2$.
