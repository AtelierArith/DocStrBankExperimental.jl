```julia
delim_string_parse(str, delim, T;
    	merge::Bool=false,
    	undefval=NaN)
```

Parse a delimited string `str` with delimiter `delim` into values of type `T` and return the answers as an array with eltype `T`

Optional keyword arguments and defaults:

```
merge::Bool=false
```

Merge repeated delimiters?

```
undefval=NaN
```

A value to subsitute for any value that cannot be `parse`d to type `T`.

See also `delim_string_parse!` for an in-place version.

### Examples

```julia
julia> delim_string_parse("1,2,3,4,5", ',', Float64)
5-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
 5.0
```
