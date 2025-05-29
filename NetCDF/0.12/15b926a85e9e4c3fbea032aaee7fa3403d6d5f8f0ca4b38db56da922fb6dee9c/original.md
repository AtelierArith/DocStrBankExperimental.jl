```
ncread!(filename, varname, d)
```

reads the values of the variable varname from file filename and writes the results to the pre-allocated array `d`

### Keyword arguments

  * `start` Vector of length `ndim(v)` setting the starting index for each dimension
  * `count` Vector of length `ndim(v)` setting the count of values to be read along each dimension. The value -1 is treated as a special case to read all values from this dimension

### Example

To read the second slice of a 3D NetCDF variable one can write:

```
d = zeros(10,10,1)
ncread!("filename","varname", d, start=[1,1,2], count = [-1,-1,1])
```
