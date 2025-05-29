```
shiftsignal(x, s)
```

Shift elements of signal x in time by a given amount s of samples and fill the spaces with zeros. For circular shifting, use circshift.

# Example

```jldoctest
julia> shiftsignal([1, 2, 3], 2)
3-element Vector{Int64}:
 0
 0
 1

julia> shiftsignal([1, 2, 3], -2)
3-element Vector{Int64}:
 3
 0
 0
```

See also [`shiftsignal!`](@ref).
