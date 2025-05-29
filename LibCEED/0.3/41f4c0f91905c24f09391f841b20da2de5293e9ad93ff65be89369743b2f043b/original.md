```
CeedVector(c::Ceed, v2::AbstractVector; mtype=MEM_HOST, cmode=COPY_VALUES)
```

Creates a new [`CeedVector`](@ref) using the contents of the given vector `v2`. By default, the contents of `v2` will be copied to the new [`CeedVector`](@ref), but this behavior can be changed by specifying a different `cmode`.
