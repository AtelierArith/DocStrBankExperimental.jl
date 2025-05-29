```julia
n = count_unique!(A)
```

Sort the array `A` in-place (if not already sorted), move unique elements to the front, and return the number of unique elements found.

`A[1:count_unique!(A)]` should return an array equivalent to `unique(A)`

### Examples

```julia
julia> A = rand(1:5, 10)
10-element Vector{Int64}:
 4
 4
 2
 3
 3
 4
 1
 5
 1
 2

julia> A = rand(1:5, 7)
7-element Vector{Int64}:
 1
 1
 4
 3
 1
 1
 4

julia> n = count_unique!(A)
3

julia> A
7-element Vector{Int64}:
 1
 3
 4
 1
 3
 4
 4

julia> A[1:n]
3-element Vector{Int64}:
 1
 3
 4
```
