```
rand(M::SymplecticStiefel; vector_at=nothing, σ = 1.0)
```

Generate a random point $p ∈ \mathrm{SpSt}(2n, 2k)$ or a random tangent vector $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ if `vector_at` is set to a point $p ∈ \mathrm{Sp}(2n)$.

A random point on $\mathrm{SpSt}(2n, 2k)$ is found by first generating a random point on the symplectic manifold $\mathrm{Sp}(2n)$, and then projecting onto the Symplectic Stiefel manifold using the [`canonical_project`](@ref) $π_{\mathrm{SpSt}(2n, 2k)}$. That is, $p = π_{\mathrm{SpSt}(2n, 2k)}(p_{\mathrm{Sp}})$.

To generate a random tangent vector in $T_p\mathrm{SpSt}(2n, 2k)$ this code exploits the second tangent vector space parametrization of [`SymplecticStiefel`](@ref), that any $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ can be written as $X = pΩ_X + p^sB_X$. To generate random tangent vectors at $p$ then, this function sets $B_X = 0$ and generates a random Hamiltonian matrix $Ω_X ∈ \mathfrak{sp}(2n,F)$ with Frobenius norm of `σ` before returning $X = pΩ_X$.
