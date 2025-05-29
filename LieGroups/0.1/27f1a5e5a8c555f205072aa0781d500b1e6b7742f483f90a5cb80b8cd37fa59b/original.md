```
LieAlgebra{𝔽, G} <: AbstractManifold{𝔽}
```

Represent the Lie algebra $\mathfrak g$, that is a $𝔽$ vector space with an associated [`lie_bracket`](@ref) $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ which fulfills

1. $[X,X] = 0$ for all $X ∈ \mathfrak g$
2. The Jacobi identity $[X, [Y,Z]] = [[X,Y],Z] = [Y, [X,Z]]$ holds for all $X, Y, Z ∈ \mathfrak g$.

The Lie algebras considered here are those related to a [`AbstractLieGroup`](@ref) $\mathcal G$, namely the tangent space $T_{\mathrm{e}}\mathcal G$ at the [`Identity`](@ref), this is internally just a `const` of the corresponding [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`).

!!! note "Convention for representing tangent vectors in the Lie algebra"
    A vector field $\mathcal X: \mathcal G → T\mathcal G$, $X(g) ∈ T_g\mathcal G$ is called a left-invariant vector field if it satisfies

    $$
    \mathcal X(λ_g(h)) = Dλ_g(h)[\mathcal X(h)], \quad\text{for all}\quad g, h ∈ \mathcal G,
    $$

    where $λ_g: \mathcal G → \mathcal G$ is the left multiplication by $g$. Hence $\mathcal X$ is determined already when $X ∈ \mathfrak g$ is given, since $\mathcal X(g) = Dλ_g(e)[X]$, cf [HilgertNeeb:2012; Definition 9.1.7](@cite).

    Throughout `LieGroups.jl`, we use this left-invariant convention to store tangent vectors at points on a Lie group as elements of the corresponding Lie algebra.


# Constructor

```
LieAlgebra(G::AbstractLieGroup)
```

Return the Lie Algebra belonging to the [`AbstractLieGroup`](@ref) `G`.
