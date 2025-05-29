```
CollectionDomain{T <: InfiniteScalarDomain} <: InfiniteArrayDomain
```

A `DataType` that stores a collection of `InfiniteScalarDomain`s characterizing a collection of infinite parameters that follows its form. This is for use with [`DependentParameters`](@ref).

**Fields**

  * `domains::Array{T}` The collection of scalar domains.
