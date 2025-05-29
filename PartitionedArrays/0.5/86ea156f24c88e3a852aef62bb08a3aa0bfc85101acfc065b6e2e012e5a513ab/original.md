```
struct DebugArray{T,N}
```

Data structure that emulates the limitations of [`MPIArray`](@ref), but that can be used on a standard sequential (a.k.a. serial) Julia session. This struct implements the Julia array interface. Like for [`MPIArray`](@ref), using `setindex!` and `getindex` on `DebugArray` is disabled since this will not be efficient in actual parallel runs (communication cost).

# Properties

The fields of this struct are private.

# Supertype hierarchy

```
DebugArray{T,N} <: AbstractArray{T,N}
```
