```
getspan(name::AbstractString) :: NTuple{2, Float64}
```

Find the time span (both ends in million year) of the geologic time.

# Example

```jldoctest
julia> getspan("Jurassic")
(201.4, 145.0)
```
