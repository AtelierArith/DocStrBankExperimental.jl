```
ncread(filename, varname)
```

reads the values of the variable `varname` from file `filename` and returns the values in an array.

### Keyword arguments

  * `start` Vector of length `ndim(v)` setting the starting index for each dimension
  * `count` Vector of length `ndim(v)` setting the count of values to be read along each dimension. The value -1 is treated as a special case to read all values along the dimension

### Example

To read the second slice of a 3D NetCDF variable, you can write:

```
ncread("filename","varname", start=[1,1,2], count = [-1,-1,1])
```
