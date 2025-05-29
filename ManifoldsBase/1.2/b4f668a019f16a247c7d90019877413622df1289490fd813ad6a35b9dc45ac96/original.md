```
sectional_curvature(M::AbstractManifold, p, X, Y)
```

Compute the sectional curvature of a manifold $\mathcal M$ at a point $p \in \mathcal M$ on two linearly independent tangent vectors at $p$. The formula reads

$$

    \kappa_p(X, Y) = \frac{⟨R(X, Y, Y), X⟩_p}{\lVert X \rVert^2_p \lVert Y \rVert^2_p - ⟨X, Y⟩^2_p}

$$

where $R(X, Y, Y)$ is the [`riemann_tensor`](@ref) on $\mathcal M$.

# Input

  * `M`:   a manifold $\mathcal M$
  * `p`:   a point $p \in \mathcal M$
  * `X`:   a tangent vector $X \in T_p \mathcal M$
  * `Y`:   a tangent vector $Y \in T_p \mathcal M$
