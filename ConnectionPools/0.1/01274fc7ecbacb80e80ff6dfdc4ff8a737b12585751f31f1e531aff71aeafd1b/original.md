GenericPool{T}(limit::Int)

A thread-safe resource pool manager for resources of type `T`.

This struct implements a resource pool, managing the acquisition and release of resources with a maximum concurrency limit.  It's designed to be used with various resource types, such as database connections or other objects that need to be managed and reused efficiently.

# Type Parameters

  * `T`: The type of resource managed by the pool.

# Fields

  * `limit::Int`: The maximum number of resources that can be in use concurrently.
  * `free::Vector{T}`: A vector containing the currently available (free) resources in the pool.
  * `taken::Set{T}`: A set containing the resources that are currently in use (taken) by users.
  * `lock::ReentrantLock`: A reentrant lock used for thread safety.  All operations on the pool are protected by this lock.
  * `condition::Threads.Condition`: A condition variable used to notify waiting tasks when a resource becomes available.

# Constructor

```julia
GenericPool{T}(limit::Int) where T
Creates a new resource pool for resources of type T with a maximum concurrency limit of limit.

# Arguments
limit::Int: The maximum number of resources allowed in the pool. Must be a positive integer.

# Throws
ArgumentError: If limit is not a positive integer.

# Example

```

julia using Pools, Redis, Dates

struct Connection     client::RedisConnection     timestamp::DateTime end

pool = GenericPool{Connection}(3) ```
