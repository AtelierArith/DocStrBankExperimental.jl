```
setarray!(v::CeedVector, mtype::MemType, cmode::CopyMode, arr)
```

Set the array used by a [`CeedVector`](@ref), freeing any previously allocated array if applicable. The backend may copy values to a different [`MemType`](@ref). See also [`syncarray!`](@ref) and [`takearray!`](@ref).

!!! warning "Avoid OWN_POINTER CopyMode"
    The [`CopyMode`](@ref) `OWN_POINTER` is not suitable for use with arrays that are allocated by Julia, since those cannot be properly freed from libCEED.

