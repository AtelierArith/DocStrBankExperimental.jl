```
Singleton(T) -> Construct{T}
Singleton(instance::T) -> Construct{T}
```

Defines an empty construct for singleton type.

This is the default constructor for `Nothing` and `Missing`.

# Examples

```jldoctest
julia> serialize(missing)
UInt8[]

julia> deserialize(Singleton(pi), UInt8[])
π = 3.1415926535897...
```
