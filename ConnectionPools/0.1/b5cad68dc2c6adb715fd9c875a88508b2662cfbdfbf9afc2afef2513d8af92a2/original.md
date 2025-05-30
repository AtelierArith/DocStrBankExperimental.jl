taken(pool::Pool{T}) where T -> Int

Return the number of resources currently taken (in use) from the pool.

This function provides a thread-safe way to check how many resources are currently in use (taken) from the pool.  It does *not* include resources that are free and available for immediate acquisition.

# Arguments

  * `pool::Pool{T}`: The resource pool to query.

# Returns

The number of taken resources in the pool.

# Thread Safety

This operation is thread-safe.

# Example

```julia
using Pools

create(::Type{Int}) = rand(1:10)

pool = GenericPool{Int}(3)
taken(pool)
```
