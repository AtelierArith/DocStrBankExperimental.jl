```
PowerManifold{𝔽,TM<:AbstractManifold,TSize,TPR<:AbstractPowerRepresentation} <: AbstractPowerManifold{𝔽,TM}
```

The power manifold $\mathcal M^{n_1× n_2 × … × n_d}$ with power geometry.  `TSize` defines the number of elements along each axis, either statically using  `TypeParameter` or storing it in a field.

For example, a manifold-valued time series would be represented by a power manifold with $d$ equal to 1 and $n_1$ equal to the number of samples. A manifold-valued image (for example in diffusion tensor imaging) would be represented by a two-axis power manifold ($d=2$) with $n_1$ and $n_2$ equal to width and height of the image.

While the size of the manifold is static, points on the power manifold would not be represented by statically-sized arrays.

# Constructor

```
PowerManifold(M::PowerManifold, N_1, N_2, ..., N_d; parameter::Symbol=:field)
PowerManifold(M::AbstractManifold, NestedPowerRepresentation(), N_1, N_2, ..., N_d; parameter::Symbol=:field)
M^(N_1, N_2, ..., N_d)
```

Generate the power manifold $M^{N_1 × N_2 × … × N_d}$. By default, a [`PowerManifold`](@ref) is expanded further, i.e. for `M=PowerManifold(N, 3)` `PowerManifold(M, 2)` is equivalent to `PowerManifold(N, 3, 2)`. Points are then 3×2 matrices of points on `N`. Providing a [`NestedPowerRepresentation`](@ref) as the second argument to the constructor can be used to nest manifold, i.e. `PowerManifold(M, NestedPowerRepresentation(), 2)` represents vectors of length 2 whose elements are vectors of length 3 of points on N in a nested array representation.

The third signature `M^(...)` is equivalent to the first one, and hence either yields a combination of power manifolds to *one* larger power manifold, or a power manifold with the default representation.

Since there is no default [`AbstractPowerRepresentation`](@ref) within this interface, the `^` operator is only available for `PowerManifold`s and concatenates dimensions.

`parameter`: whether a type parameter should be used to store `n`. By default size is stored in a field. Value can either be `:field` or `:type`.
