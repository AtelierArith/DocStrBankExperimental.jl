clean!(resource::T) where T

Clean up resources associated with a resource of type `T`.

This function is called automatically by the pool in the following situations:

  * When a resource fails validation (as determined by the `check` function).
  * When a resource is removed from the pool (e.g., during pool draining or when the pool's limit is reduced).

You *should* implement this method to release any external resources held by the resource (e.g., closing connections, freeing memory, etc.).  If you do not implement this method, the default implementation will do nothing.

# Arguments

  * `resource::T`: The resource to clean up.

# Generic Method

A generic `clean!(::T) where T` method is provided, which does nothing. It is *strongly recommended* that you implement a specific `clean!` method if your resource requires any cleanup.

# Example

```julia
using Pools, Redis, Dates
import Pools: create, clean!

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

function clean!(redis::Connection)
    Redis.disconnect(redis.client)
end
```
