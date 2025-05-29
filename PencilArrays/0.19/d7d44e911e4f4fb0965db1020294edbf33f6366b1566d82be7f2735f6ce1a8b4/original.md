```
GlobalPencilArray{T,N} <: AbstractArray{T,N}
```

Alias for an `OffsetArray` wrapping a [`PencilArray`](@ref).

Unlike `PencilArray`s, `GlobalPencilArray`s take *global* indices, which in general don't start at 1 for a given MPI process.

The [`global_view`](@ref) function should be used to create a `GlobalPencilArray` from a `PencilArray`.
