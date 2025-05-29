```julia
delim_string_function(f, str, delim, T;
    	merge::Bool=false,
```

Parse a delimited string `str` with delimiter `delim` into substrings that will then be operated upon by function `f`. The results of `f` will be returned in an array with eltype `T`.

### Examples

```julia
julia> delim_string_function(x -> delim_string_parse(x, ',', Int32, undefval=0), "1,2,3,4
5,6,7,8
9,10,11,12
13,14,15,16", '
', Array{Int32,1})
4-element Vector{Vector{Int32}}:
 [1, 2, 3, 4]
 [5, 6, 7, 8]
 [9, 10, 11, 12]
 [13, 14, 15, 16]
```
