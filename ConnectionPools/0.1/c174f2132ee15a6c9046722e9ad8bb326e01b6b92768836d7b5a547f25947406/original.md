free(pool::Pool{T}) where T -> Int

Return the number of free resources currently available in the pool.

This function provides a thread-safe way to check how many resources are currently available for immediate acquisition in the pool. It does *not* include resources that are currently in use (taken).

# Arguments

  * `pool::Pool{T}`: The resource pool to query.

# Returns

The number of free resources in the pool.

# Thread Safety

This operation is thread-safe.

# Example

```julia
using Pools

create(::Type{Int}) = rand(1:10)

pool = GenericPool{Int}(3)
free(pool)
```
