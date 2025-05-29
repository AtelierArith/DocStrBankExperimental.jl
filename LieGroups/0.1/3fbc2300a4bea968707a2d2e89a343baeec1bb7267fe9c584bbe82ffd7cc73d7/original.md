```
adjoint(G::AbstractLieGroup, g, X)
adjoint!(G::AbstractLieGroup, Y, g, X)
```

Compute the adjoint $\mathrm{Ad}(g): \mathfrak g → \mathfrak g$, which is defined as the differential [`diff_conjugate`](@ref) of the [`conjugate`](@ref) $c_g(h) = g∘h∘g^{-1}$ evaluated at the [`Identity`](@ref) $h=\mathrm{e}$. The operation can be performed in-place of `Y`.

$$
  \mathrm{Ad}(g)[X] = D c_g(\mathrm{e}) [X], \qquad X ∈ \mathfrak g.
$$

see [HilgertNeeb:2012; Section 9.2.3](@cite).

On matrix Lie groups the adjoint reads $\mathrm{Ad}(g)[X] = g∘X∘g^{-1}$.
