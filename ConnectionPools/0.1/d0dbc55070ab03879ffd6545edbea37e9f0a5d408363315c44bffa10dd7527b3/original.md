ConnectionPool{T}(limit::Int) where T -> GenericPool{T}

Alias for `GenericPool{T}`.

This function is an alias for `GenericPool{T}` and is provided for convenience.  It creates a new resource pool for resources of type `T` with a maximum concurrency limit of `limit`.

# Arguments

  * `limit::Int`: The maximum number of resources allowed in the pool. Must be a positive integer.

# Throws

  * `ArgumentError`: If `limit` is not a positive integer.
