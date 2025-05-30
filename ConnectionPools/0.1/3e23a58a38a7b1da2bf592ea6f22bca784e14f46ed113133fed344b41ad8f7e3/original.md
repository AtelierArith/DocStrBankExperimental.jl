drain!(pool::Pool{T}) where T

Drain the resource pool, releasing and finalizing all resources.

This function releases all resources currently held by the pool, both free and taken. It waits for all taken resources to be released back to the pool before finalizing them. This is typically used when you want to shut down the pool or when you need to ensure that all resources are properly cleaned up.

# Arguments

  * `pool::Pool{T}`: The resource pool to drain.

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
clean!(redis::Connection) = Redis.disconnect(redis.client)

pool = ConnectionPool{Connection}(3)

withresource(pool) do redis
    ping(redis.client)
end

drain!(pool)
```
