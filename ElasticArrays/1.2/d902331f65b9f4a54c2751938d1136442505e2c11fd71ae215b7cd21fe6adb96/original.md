```
ElasticArray{T,N,M} <: DenseArray{T,N}
```

An `ElasticArray` can grow/shrink in its last dimension. `N` is the total number of dimensions, `M == N - 1` the number of non-resizable dimensions.

Constructors:

```
ElasticArray{T}(dims::Integer...)
convert(ElasticArray, A::AbstractArray)
```
