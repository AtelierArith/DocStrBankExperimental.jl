```
pos(vector) -> vector
```

Returns new vector such that all the NaN and negative values in `vector` to zero. Mimicks max(0, vector) in Matlab. If vector is a scalar returns a scalar.

# Example

```jldoctest
julia> vector = [1, 2, 3, NaN, -1 ]

julia> pos(vector)
5-element Vector{Float64}:
 1.0
 2.0
 3.0
 0.0
 0.0
```
