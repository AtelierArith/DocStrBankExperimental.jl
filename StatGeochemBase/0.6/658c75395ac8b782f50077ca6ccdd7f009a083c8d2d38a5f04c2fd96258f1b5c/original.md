```julia
delim_string_parse!(result, str, delim, [T];
    	offset::Integer=0,
    	merge::Bool=false,
    	undefval=NaN)
```

Parse a delimited string `str` with delimiter `delim` into values of type `T` and return the answers in a pre-allocated `result` array provided as input.

If `T` is not specified explicitly, the `eltype` of the `result` array will be used by default.

Optional keyword arguments and defaults:

```
offset::Integer=0
```

Start writing the parsed results into `result` at index `1+offset`

```
merge::Bool=false
```

Merge repeated delimiters?

```
undefval=NaN
```

A value to subsitute for any value that cannot be `parse`d to type `T`.

See also `delim_string_parse` for a non-in-place version that will automatically allocate a result array.

### Examples

```julia
julia> A = zeros(100);

julia> n = delim_string_parse!(A, "1,2,3,4,5", ',', Float64)
5

julia> A[1:n]
5-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
 5.0
```
