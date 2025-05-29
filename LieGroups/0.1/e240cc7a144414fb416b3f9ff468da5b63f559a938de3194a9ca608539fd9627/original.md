```
SpecialEuclideanGroup{T}
```

The special Euclidean group $\mathrm{SE}(n) = \mathrm{SO}(n) ⋉ \mathcal T(n)$ is the Lie group consisting of the [`LeftSemidirectProductGroupOperation`](@ref) of the [`SpecialOrthogonalGroup`](@ref) and the [`TranslationGroup`](@ref) together with the [`GroupOperationAction`](@ref)`{`[`LeftGroupOperationAction`](@ref)`}`.

To be precise, the group operation is defined on $\mathrm{SO}(n) ⋉ \mathcal T(n)$ as follows:

$$
(r_1, t_1) ⋅ (r_2, t_2) = (r_1∘r_2, t_1 + r_1⋅t_2),
$$

where $r_1,r_2 ∈ \mathrm{SO}(n)$ and $t_1,t_2 ∈ \mathcal T(n)$

Analogously you can write this on elements of $\mathrm{SO}(n) ⋊ \mathcal T(n)$ as

$$
(t_1, r_1) ⋅ (t_2, r_2) = (t_1 + r_1⋅s_2, r_1∘r_2)
$$

Both these cases can be represented in a single matrix in [affine form](https://en.wikipedia.org/wiki/Affine_group#Matrix_representation)

$$
g = \begin{pmatrix} r & t\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
\qquad r ∈ \mathrm{SO}(n), t ∈ \mathcal T(n),
$$

where $\mathbf{0}_n ∈ ℝ^n$ denotes the vector containing zeros.

We refer also in general to elements on $\mathrm{SE}(n)$ as $g$ and their rotation and translation components as $r$ and $t$, respectively.

# Constructor

```
SpecialEuclideanGroup(n::Int; variant=:left, kwargs...)
SpecialOrthogonalGroup(n; kwargs...) ⋉ TranslationGroup(n; kwargs...)
TranslationGroup(n; kwargs...) ⋊ SpecialOrthogonalGroup(n; kwargs...)
```

Generate special Euclidean group $\mathrm{SE}(n) = \mathrm{SO}(n) ⋉ \mathcal T(n)$, where the first constructor is equivalent to the second.

All keyword arguments in `kwargs...` are passed on to [`Rotations`](@extref `Manifolds.Rotations`) as well.

The default representation for $\mathrm{SE}(n)$ is the affine form. Alternatively you can use the `ArrayPartition` from [`RecursiveArrayTools.jl`](https://docs.sciml.ai/RecursiveArrayTools/stable/) to work on $(r,t)$. or for $\mathcal T(n) ⋊ \mathrm{SO}(n)$ using the `ArrayPartition`s $(t,r)$; which corresponds to setting `variant=:right` in the first constructor.
