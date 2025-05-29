```
get_coordinates(M::Rotations, p, X)
get_coordinates(M::OrthogonalMatrices, p, X)
get_coordinates(M::UnitaryMatrices, p, X)
```

Extract the unique tangent vector components $X^i$ at point `p` on [`Rotations`](@ref) $\mathrm{SO}(n)$ from the matrix representation `X` of the tangent vector.

The basis on the Lie algebra $𝔰𝔬(n)$ is chosen such that for $\mathrm{SO}(2)$, $X^1 = θ = X_{21}$ is the angle of rotation, and for $\mathrm{SO}(3)$, $(X^1, X^2, X^3) = (X_{32}, X_{13}, X_{21}) = θ u$ is the angular velocity and axis-angle representation, where $u$ is the unit vector along the axis of rotation.

For $\mathrm{SO}(n)$ where $n ≥ 4$, the additional elements of $X^i$ are $X^{j (j - 3)/2 + k + 1} = X_{jk}$, for $j ∈ [4,n], k ∈ [1,j)$.
