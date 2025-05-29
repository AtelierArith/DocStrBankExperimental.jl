```julia
parsedlm(str::AbstractString, delimiter::Char, T::Type=Float64; rowdelimiter::Char='\n', merge::Bool=false)
```

Parse a string delimited by both row and column into a single (2-D) matrix. Default column delimiter is newline. Similar to `readdlm`, but operating on a string instead of a file.

### Examples

```julia
julia> parsedlm("1,2,3
4,5,6
7,8,9
", ',', Float64)
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> parsedlm("1,2,3,4
5,6,7,8
9,10,11,12
13,14,15,16", ',', Int64)
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16
```
