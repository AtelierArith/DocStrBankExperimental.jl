withresource(f::Function, pool::Pool{T}) where T

Execute a function with a resource from the pool, automatically handling acquisition and release.

This function provides a safe and convenient way to use resources from the pool.  It acquires a resource, passes it to the provided function `f`, and *guarantees* that the resource is released back to the pool, even if an error occurs within the function.  This is the *recommended* way to work with pooled resources, as it prevents resource leaks and simplifies resource management.

# Arguments

  * `f::Function`: A function that accepts a resource of type `T` as its argument. This function performs the operations you want to do with the resource.
  * `pool::Pool{T}`: The resource pool to acquire the resource from.

# Returns

The value returned by the function `f`.

# Throws

  * Exceptions thrown by the function `f`.  These exceptions will be propagated after the resource is released.
  * `MethodError`: If the `create(::Type{T})` or `check(resource::T)` functions are not implemented for the resource type `T`.

# Example

```julia

using Redis, Dates

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now())

pool = ConnectionPool{Connection}(3)

withresource(pool) do redis
    ping(redis.client)
end
```
