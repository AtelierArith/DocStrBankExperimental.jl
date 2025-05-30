limit(pool::Pool{T}) where T -> Int

Return the maximum number of resources that the pool can hold concurrently.

This function returns the `limit` of the pool, which represents the maximum number of resources that can be in use (taken) at any given time.

# Arguments

  * `pool::Pool{T}`: The resource pool to query.

# Returns

The maximum number of concurrent resources allowed by the pool.

# Thread Safety

This operation is thread-safe.  Access to the `pool.limit` field is inherently atomic in Julia.

# Example

```julia
using Pools

create(::Type{Int}) = rand(1:10)

pool = GenericPool{Int}(5)
limit(pool)
```
