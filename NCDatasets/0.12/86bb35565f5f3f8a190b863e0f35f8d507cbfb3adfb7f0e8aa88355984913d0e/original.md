```
cv = coord(v::Union{CFVariable,Variable},standard_name)
```

Find the coordinate of the variable `v` by the standard name `standard_name` or some [standardized heuristics based on units](https://web.archive.org/web/20190918144052/http://cfconventions.org/cf-conventions/cf-conventions.html#latitude-coordinate). If the heuristics fail to detect the coordinate, consider to modify the netCDF file to add the `standard_name` attribute. All dimensions of the coordinate must also be dimensions of the variable `v`.

## Example

```julia
using NCDatasets
ds = NCDataset("file.nc")
ncv = ds["SST"]
lon = coord(ncv,"longitude")[:]
lat = coord(ncv,"latitude")[:]
v = ncv[:]
close(ds)
```
