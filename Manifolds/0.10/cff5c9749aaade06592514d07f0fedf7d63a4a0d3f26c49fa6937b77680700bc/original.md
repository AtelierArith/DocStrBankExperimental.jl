```
inner(::SymplecticGrassmann, p, X, Y)
```

Compute the Riemannian inner product $g^{\mathrm{SpGr}}_p(X,Y)$ on the [`SymplecticGrassmann`](@ref) manifold `\mathrm{SpGr}``.

For the case where $p$ is represented by a point on the [`SymplecticStiefel`](@ref) manifold acting as a representant of its equivalence class $[p] \in \mathrm{SpGr}$ and the tangent vectors $X,Y \in \mathrm{Hor}_p^π\operatorname{SpSt}(2n,2k)$ are horizontal tangent vectors.

Then the inner product reads according to Proposition Lemma 4.8 [BendokatZimmermann:2021](@cite).

$$
g^{\mathrm{SpGr}}_p(X,Y) = \operatorname{tr}\bigl(
        (p^{\mathrm{T}}p)^{-1}X^{\mathrm{T}}(I_{2n} - pp^+)Y
    \bigr),
$$

where $I_{2n}$ denotes the identity matrix and $(⋅)^+$ the [`symplectic_inverse`](@ref).
