```
gather(x::PencilArray{T, N}, [root::Integer=0]) -> Array{T, N}
```

Gather data from all MPI processes into one (big) array.

Data is received by the `root` process.

Returns the full array on the `root` process, and `nothing` on the other processes.

Note that `gather` always returns a base `Array`, even when the `PencilArray` wraps a different kind of array (e.g. a `CuArray`).

This function can be useful for testing, but it shouldn't be used with very large datasets!
