```
chain_writer(dafs::AbstractVector{<:DafReader}; name::Maybe{AbstractString} = nothing)::DafWriter
```

Create a chain wrapper for a chain of [`DafReader`](@ref) data, presenting them as a single [`DafWriter`](@ref). This acts similarly to [`chain_reader`](@ref), but requires the final entry in the chain to be a [`DafWriter`](@ref). Any modifications or additions to the chain are directed only at this final writer.

!!! note
    Deletions are only allowed for data that exists only in the final writer. That is, it is impossible to delete from a chain something that exists in any of the readers; it is only possible to override it.

