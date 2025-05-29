```
rand(::SymplecticStiefel; vector_at=nothing, σ=1.0)
```

Generate a random point on $\mathrm{Sp}(2n)$ or a random tangent vector $X \in T_p\mathrm{Sp}(2n)$ if `vector_at` is set to a point $p \in \mathrm{Sp}(2n)$.

A random point on $\mathrm{Sp}(2n)$ is constructed by generating a random Hamiltonian matrix $Ω \in \mathfrak{sp}(2n,F)$ with norm `σ`, and then transforming it to a symplectic matrix by applying the Cayley transform

$$
  \operatorname{cay}: \mathfrak{sp}(2n,F) → \mathrm{Sp}(2n),
  \ \Omega \mapsto (I - \Omega)^{-1}(I + \Omega).
$$

To generate a random tangent vector in $T_p\mathrm{Sp}(2n)$, this code employs the second tangent vector space parametrization of [`SymplecticMatrices`](@ref). It first generates a random symmetric matrix $S$ by `S = randn(2n, 2n)` and then symmetrizes it as `S = S + S'`. Then $S$ is normalized to have Frobenius norm of `σ` and `X = pJS` is returned, where `J` is the [`SymplecticElement`](@ref).
