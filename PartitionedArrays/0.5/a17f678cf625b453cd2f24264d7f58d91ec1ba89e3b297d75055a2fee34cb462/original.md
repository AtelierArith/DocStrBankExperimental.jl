```
struct PVector{V,A,B,...}
```

`PVector` (partitioned vector) is a type representing a vector whose entries are distributed (a.k.a. partitioned) over different parts for distributed-memory parallel computations.

This type overloads numerous array-like operations with corresponding parallel implementations.

# Properties

  * `vector_partition::A`
  * `index_partition::B`

`vector_partition[i]` contains the vector of local values of the `i`-th part in the data distribution. The first type parameter `V` corresponds to `typeof(values[i])` i.e. the vector type used to store the local values. The item `index_partition[i]` implements the [`AbstractLocalIndices`](@ref) interface providing information about the local, own, and ghost indices in the `i`-th part.

The rest of fields of this struct and type parameters are private.

# Supertype hierarchy

```
PVector{V,A,B,...} <: AbstractVector{T}
```

with `T=eltype(V)`.
