```
neg(vector) -> vector
```

Returns new vector such that all the NaN and positive values in `vector` to zero. Mimicks min(0, vector) in Matlab. If vector is a scalar returns a scalar.

# Example

```jldoctest
julia> vector = [1, 2, 3, NaN, -1 ]

julia> neg(vector)
5-element Vector{Float64}:
0.0
0.0
0.0
0.0
-1.0
```
