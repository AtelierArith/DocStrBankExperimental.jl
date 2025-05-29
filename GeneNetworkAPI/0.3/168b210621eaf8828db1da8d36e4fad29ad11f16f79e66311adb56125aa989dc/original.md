```
check_gn(url::AbstractString)
```

Check if GeneNetwork server is responding properly.

Returns the HTTP status code (`200` if successful) and prints a message.

# Example

```jldoctest
julia> check_gn()
GeneNetwork is alive.
200
```
