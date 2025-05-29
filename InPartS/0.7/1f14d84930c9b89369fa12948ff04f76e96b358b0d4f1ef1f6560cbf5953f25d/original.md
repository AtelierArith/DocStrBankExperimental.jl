```
AbstractSeqRegistrar{T <: Integer}
```

Subtype for [`AbstractRegistrar`](@ref)s that use sequential integer IDs. Comes with a helper function [`_nextid!`](@ref) that returns the next available ID and increases the internal counter (called `next_id`) by one. Other internal state changes should be taken care of by the `get_id!` API function method for each subtype.

For implementations, see [`SimpleRegistrar`](@ref), [`LineageRegistrar`](@ref) and [`LineageCoordRegistrar`](@ref).
