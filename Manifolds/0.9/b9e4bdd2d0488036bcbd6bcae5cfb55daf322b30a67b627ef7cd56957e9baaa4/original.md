```
SpecialEuclidean(n)
```

Special Euclidean group $\mathrm{SE}(n)$, the group of rigid motions.

$\mathrm{SE}(n)$ is the semidirect product of the [`TranslationGroup`](@ref) on $ℝ^n$ and [`SpecialOrthogonal`](@ref)`(n)`

$$
\mathrm{SE}(n) ≐ \mathrm{T}(n) ⋊_θ \mathrm{SO}(n),
$$

where $θ$ is the canonical action of $\mathrm{SO}(n)$ on $\mathrm{T}(n)$ by vector rotation.

This constructor is equivalent to calling

```julia
Tn = TranslationGroup(n)
SOn = SpecialOrthogonal(n)
SemidirectProductGroup(Tn, SOn, RotationAction(Tn, SOn))
```

Points on $\mathrm{SE}(n)$ may be represented as points on the underlying product manifold $\mathrm{T}(n) × \mathrm{SO}(n)$. For group-specific functions, they may also be represented as affine matrices with size `(n + 1, n + 1)` (see [`affine_matrix`](@ref)), for which the group operation is [`MultiplicationOperation`](@ref).
