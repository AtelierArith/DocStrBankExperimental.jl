```julia
VectorOfArray(u::AbstractVector)
```

A `VectorOfArray` is an array which has the underlying data structure `Vector{AbstractArray{T}}` (but, hopefully, concretely typed!). This wrapper over such data structures allows one to lazily act like it's a higher-dimensional vector, and easily convert it to different forms. The indexing structure is:

```julia
A.u[i] # Returns the ith array in the vector of arrays
A[j, i] # Returns the jth component in the ith array
A[j1, ..., jN, i] # Returns the (j1,...,jN) component of the ith array
```

which presents itself as a column-major matrix with the columns being the arrays from the vector. The `AbstractArray` interface is implemented, giving access to `copy`, `push`, `append!`, etc. functions, which act appropriately. Points to note are:

  * The length is the number of vectors, or `length(A.u)` where `u` is the vector of arrays.
  * Iteration follows the linear index and goes over the vectors

Additionally, the `convert(Array,VA::AbstractVectorOfArray)` function is provided, which transforms the `VectorOfArray` into a matrix/tensor. Also, `vecarr_to_vectors(VA::AbstractVectorOfArray)` returns a vector of the series for each component, that is, `A[i,:]` for each `i`. A plot recipe is provided, which plots the `A[i,:]` series.

There is also support for `VectorOfArray` constructed from multi-dimensional arrays

```julia
VectorOfArray(u::AbstractArray{AT}) where {T, N, AT <: AbstractArray{T, N}}
```

where `IndexStyle(typeof(u)) isa IndexLinear`.
