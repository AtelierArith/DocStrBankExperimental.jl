```
MPIArray{T,N}
```

Represent an array of element type `T` and number of dimensions `N`, where each item in the array is stored in a separate MPI process. I.e., each MPI rank stores only one item. For arrays that can store more than one item per rank see [`PVector`](@ref) or [`PSparseMatrix`](@ref). This struct implements the Julia array interface. However, using `setindex!` and `getindex!` is disabled for performance reasons (communication cost).

# Properties

The fields of this struct (and the inner constructors) are private. To generate an instance of `MPIArray` use function [`distribute_with_mpi`](@ref).

# Supertype hierarchy

```
MPIArray{T,N} <: AbstractArray{T,N}
```
