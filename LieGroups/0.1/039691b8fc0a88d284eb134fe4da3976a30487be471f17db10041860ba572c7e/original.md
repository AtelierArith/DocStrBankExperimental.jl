```
jacobian_conjugate(G::AbstractLieGroup, g, h; basis::AbstractBasis=DefaultLieAlgebraOrthogonalBasis(); X=zero_vector(LieAlgebar(G)))
jacobian_conjugate!(G::AbstractLieGroup, J, g, h; basis::AbstractBasis=DefaultLieAlgebraOrthogonalBasis(); X=zero_vector(LieAlgebar(G)))
```

Compute the Jacobian of the [`conjugate`](@ref) $c_g(h) = g∘h∘g^{-1}$, with respect to an [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) of the [`LieAlgebra`](@ref).

A default is implemented using [`diff_conjugate`](@ref) $D(c_g(h))[X]$: the $j$th column of of the Jacobian matrix $J$ are given by the coefficients of the tangent vector `D(c_g(h))[X_j]``with respect to the basis``B``, where``X_j``is the``j``th basis vector of``B``.

!!! note
    For the case that `h` is the [`Identity`](@ref) and the relation of $D(c_g(h))[X]$ to the [`adjoint`](@ref) $\mathrm{Ad}(g)$, the Jacobian then sometimes called “adjoint matrix”, e.g. in [SolaDerayAtchuthan:2021](@cite), when choosing as a basis the [`DefaultLieAlgebraOrthogonalBasis`](@ref)`()` that is used for [`hat`](@ref) and [`vee`](@ref).


## Keyword arguments

  * `X=zero_vector(LieAlgebra(G))` pass an interims memory to store the Lie algebra tangent vector in.
