```
array_cache(a::AbstractArray)
```

Returns a cache object to be used in the [`getindex!`](@ref) function. It defaults to

```
array_cache(a::T) where T = nothing
```

for types `T` such that `uses_hash(T) == Val(false)`, and

```
function array_cache(a::T) where T
  hash = Dict{UInt,Any}()
  array_cache(hash,a)
end
```

for types `T` such that `uses_hash(T) == Val(true)`, see the [`uses_hash`](@ref) function. In the later case, the type `T` should implement the following signature:

```
array_cache(hash::Dict,a::AbstractArray)
```

where we pass a dictionary (i.e., a hash table) in the first argument. This hash table can be used to test if the object `a` has already built a cache and re-use it as follows

```
id = objectid(a)
if haskey(hash,id)
  cache = hash[id] # Reuse cache
else
  cache = ... # Build a new cache depending on your needs
  hash[id] = cache # Register the cache in the hash table
end
```

This mechanism is needed, e.g., to re-use intermediate results in complex lazy operation trees. In multi-threading computations, a different hash table per thread has to be used in order to avoid race conditions.
