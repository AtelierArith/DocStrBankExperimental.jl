acquire!(pool::Pool{T}) where T -> T

Acquire a resource from the pool.

This function attempts to retrieve a resource from the pool.  It will reuse valid cached resources if available, create new resources if the pool is below its limit, or block until a resource becomes available if the pool is at its limit and no valid cached resources are available.

# Arguments

  * `pool::Pool{T}`: The resource pool to acquire from.

# Returns

A resource of type `T`.

# Throws

  * `MethodError`: If the `create(::Type{T})` function is not implemented for the resource type `T`.  This function is essential for the `Pool` to create new resources when needed.  See the documentation for `create` for more details.
  * Exceptions thrown by the `check(resource::T)` function. If `check` throws an exception, the resource is considered invalid and discarded.

# Thread Safety

This operation is thread-safe.

# Example

```julia
using Redis, Dates

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now())
check(redis::Connection) = ping(redis.client)

pool = ConnectionPool{Connection}(3)
conn = acquire!(pool)
```
