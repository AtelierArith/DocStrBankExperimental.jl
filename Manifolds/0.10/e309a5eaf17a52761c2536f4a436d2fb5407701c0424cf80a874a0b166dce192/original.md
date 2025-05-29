```
Euclidean{T,𝔽} <: AbstractManifold{𝔽}
```

Euclidean vector space.

# Constructor

```
Euclidean(n)
```

Generate the $n$-dimensional vector space $ℝ^n$.

```
Euclidean(n₁,n₂,...,nᵢ; field=ℝ, parameter::Symbol = :field)
𝔽^(n₁,n₂,...,nᵢ) = Euclidean(n₁,n₂,...,nᵢ; field=𝔽)
```

Generate the vector space of $k = n_1 ⋅ n_2 ⋅ … ⋅ n_i$ values, i.e. the manifold $𝔽^{n_1, n_2, …, n_i}$, $𝔽\in\{ℝ,ℂ\}$, whose elements are interpreted as $n_1 × n_2 × … × n_i$ arrays. For $i=2$ we obtain a matrix space. The default `field=ℝ` can also be set to `field=ℂ`. The dimension of this space is $k \dim_ℝ 𝔽$, where $\dim_ℝ 𝔽$ is the [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) of the field $𝔽$.

`parameter`: whether a type parameter should be used to store `n`. By default size is stored in type. Value can either be `:field` or `:type`.

```
Euclidean(; field=ℝ)
```

Generate the 1D Euclidean manifold for an `ℝ`-, `ℂ`-valued  real- or complex-valued immutable values (in contrast to 1-element arrays from the constructor above).
