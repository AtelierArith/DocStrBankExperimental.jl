```
varbyattrib(ds, attname = attval)
```

Returns a list of variable(s) which has the attribute `attname` matching the value `attval` in the dataset `ds`. The list is empty if the none of the variables has the match. The output is a list of `CFVariable`s.

# Examples

Load all the data of the first variable with standard name "longitude" from the NetCDF file `results.nc`.

```julia-repl
julia> ds = NCDataset("results.nc", "r");
julia> data = varbyattrib(ds, standard_name = "longitude")[1][:]
```
