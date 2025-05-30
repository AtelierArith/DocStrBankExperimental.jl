check(resource::T) where T

Check the validity of a resource of type `T`.

This function is called automatically by the pool during resource acquisition (`acquire!`).  If `check` fails, the resource is considered invalid, and the pool will attempt to create a new resource (or retrieve another free resource).  It is essential to implement this method to ensure that the pool only provides valid resources to users.

# Arguments

  * `resource::T`: The resource to validate.

# Generic Method

A generic `check(::T) where T` method is provided, which does nothing.  This means that if you do not define a specific `check` method for your resource type, all resources will be considered valid.  While this might seem convenient, it is *strongly recommended* that you implement a specific `check` method that performs appropriate checks for your resource type.  Relying on the generic method without proper validation can lead to unexpected errors and resource leaks.

# Example

```julia
using Pools, Redis, Dates
import Pools: create, check

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

function check(redis::Connection)
    ping(redis.client)
end
```
