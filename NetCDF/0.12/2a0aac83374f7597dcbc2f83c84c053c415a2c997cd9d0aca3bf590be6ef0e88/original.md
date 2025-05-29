```
ncwrite(x::Array,fil::AbstractString,vname::AbstractString)
```

Writes the array `x` to the file `fil` and variable `vname`.

### Keyword arguments

  * `start` Vector of length `ndim(v)` setting the starting index for writing for each dimension
  * `count` Vector of length `ndim(v)` setting the count of values to be written along each dimension. The value -1 is treated as a special case to write all values along the dimension. This is usually inferred by the given array size.
