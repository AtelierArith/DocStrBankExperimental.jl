change!(resource::T) where T

Change the state of a resource of type `T` during releasing before it is reused.

This function is called automatically by the pool when a resource is returned to the pool via `release!`.  It provides an opportunity to update the resource's internal state, such as resetting connection parameters, change timestamps, etc.

You *should* implement this method if your resource requires any state changes before it can be reused.  If no update is needed, you can leave this method unimplemented, and the default implementation will do nothing.

# Arguments

  * `resource::T`: The resource to modify.

# Generic Method

A generic `change!(::T) where T` method is provided, which does nothing. This serves as a default implementation so that if you do not define a specific `change!` method for your resource type. However, it is *strongly recommended* that you implement a specific `change!` method if your resource requires any state changes.

# Example

```julia
using Pools, Redis, Dates
import Pools: create, change!

mutable struct Connection
    client::RedisConnection
    timestamp::DateTime
end

function change!(redis::Connection)
    redis.timestamp = now()
end
```
