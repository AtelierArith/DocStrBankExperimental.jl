release!(pool::Pool{T}, resource::T)

Release a resource back to the pool.

This function returns a resource to the pool, making it available for reuse.  It changes the resource's state (using the `change!` function) and notifies any waiting tasks that a resource has become available.

# Arguments

  * `pool::Pool{T}`: The resource pool to release the resource to.
  * `resource::T`: The resource to release.

# Throws

  * `ArgumentError`: If the provided `resource` does not belong to the pool (i.e., it was not acquired from this pool).
  * Exceptions thrown by the `change!(resource::T)` function.

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
change!(redis::Connection) = redis.timestamp = now()

pool = ConnectionPool{Connection}(3)
conn = acquire!(pool)
release!(pool, conn)
```
