```
chunk(x, n; [dims])
chunk(x; [size, dims])
```

Split `x` into `n` parts or alternatively, if `size` is an integer, into equal chunks of size `size`.  The parts contain the same number of elements except possibly for the last one that can be smaller.

In case `size` is a collection of integers instead, the elements of `x` are split into chunks of the given sizes.

If `x` is an array, `dims` can be used to specify along which dimension to  split (defaults to the last dimension).

# Examples

```jldoctest
julia> chunk(1:10, 3)
3-element Vector{UnitRange{Int64}}:
 1:4
 5:8
 9:10

julia> chunk(1:10; size = 2)
5-element Vector{UnitRange{Int64}}:
 1:2
 3:4
 5:6
 7:8
 9:10

julia> x = reshape(collect(1:20), (5, 4))
5×4 Matrix{Int64}:
 1   6  11  16
 2   7  12  17
 3   8  13  18
 4   9  14  19
 5  10  15  20

julia> xs = chunk(x, 2, dims=1)
2-element Vector{SubArray{Int64, 2, Matrix{Int64}, Tuple{UnitRange{Int64}, Base.Slice{Base.OneTo{Int64}}}, false}}:
 [1 6 11 16; 2 7 12 17; 3 8 13 18]
 [4 9 14 19; 5 10 15 20]

julia> xs[1]
3×4 view(::Matrix{Int64}, 1:3, :) with eltype Int64:
 1  6  11  16
 2  7  12  17
 3  8  13  18

julia> xes = chunk(x; size = 2, dims = 2)
2-element Vector{SubArray{Int64, 2, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, UnitRange{Int64}}, true}}:
 [1 6; 2 7; … ; 4 9; 5 10]
 [11 16; 12 17; … ; 14 19; 15 20]

julia> xes[2]
5×2 view(::Matrix{Int64}, :, 3:4) with eltype Int64:
 11  16
 12  17
 13  18
 14  19
 15  20

julia> chunk(1:6; size = [2, 4])
2-element Vector{UnitRange{Int64}}:
 1:2
 3:6
```
