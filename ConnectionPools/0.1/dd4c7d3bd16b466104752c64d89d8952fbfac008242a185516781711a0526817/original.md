create(::Type{T}) where T -> T

Create a new instance of type `T`.

This function is called automatically by the pool when a new resource is needed (e.g., when a resource is acquired and the pool is empty or below its limit).  You *must* implement this method for any type `T` that you want to store in a `Pool`.

# Arguments

  * `::Type{T}`: The type of the resource to create.  This is a type parameter, not an instance of the type.

# Returns

A new resource of type `T`.

# Throws

  * `MethodError`: If this function is not implemented for the given type `T`.

# Example

```julia

using Pools, Redis, Dates
import Pools: create

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now())
```
