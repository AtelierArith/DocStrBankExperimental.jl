```
AbstractBasis{T,N} <: AbstractArray{T,N}
```

The supertype of all types representing bases whose elements are of type `T`. Bases are needed for linear combinations of type `DenseLinear`.

All subtypes of `AbstractBasis` must implement the [abstract arrays interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array). For a given basis `b`, `b[i]` is the i-th basis element. Mapping from basis elements to indices is one via the `toindex` function. The parameter `N == ndims(b)` specifies how many indices are used to index elements of a basis `b`.

See also [`Basis`](@ref), [`TensorBasis`](@ref), [`toindex`](@ref), `Base.ndims`.
