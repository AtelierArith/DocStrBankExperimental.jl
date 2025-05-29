```
syncarray!(v::CeedVector, mtype::MemType)
```

Sync the [`CeedVector`](@ref) to a specified [`MemType`](@ref). This function is used to force synchronization of arrays set with [`setarray!`](@ref). If the requested memtype is already synchronized, this function results in a no-op.
