```
rpad_constant(v::AbstractArray, n::Union{Integer, Tuple}, val = 0; dims=:)
```

Return the given sequence padded with `val` along the dimensions `dims` up to a maximum length in each direction specified by `n`.

# Examples

```jldoctest
julia> rpad_constant([1, 2], 4, -1) # passing with -1 up to size 4
4-element Vector{Int64}:
  1
  2
 -1
 -1

julia> rpad_constant([1, 2, 3], 2) # no padding if length is already greater than n
3-element Vector{Int64}:
 1
 2
 3

julia> rpad_constant([1 2; 3 4], 4; dims=1) # padding along the first dimension
4×2 Matrix{Int64}:
 1  2
 3  4
 0  0
 0  0

julia> rpad_constant([1 2; 3 4], 4) # padding along all dimensions by default
4×4 Matrix{Int64}:
 1  2  0  0
 3  4  0  0
 0  0  0  0
 0  0  0  0
```
