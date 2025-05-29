```
buffergeo(D::GMTdataset; width=0, unit=:m, np=120, flatstart=false, flatend=false, epsg::Integer=0, tol=0.01)
```

or

```
buffergeo(line::Matrix; width=0, unit=:m, np=120, flatstart=false, flatend=false, proj::String="", epsg::Integer=0, tol=0.01)
```

or

```
buffergeo(fname::String; width=0, unit=:m, np=120, flatstart=false, flatend=false, proj::String="", epsg::Integer=0, tol=0.01)
```

Computes a buffer arround a poly-line. This calculation is performed on a ellipsoidal Earth (or other planet) using the GeographicLib (via PROJ4) so it should be very accurate.

### Parameters

  * `D` | `line` | fname: - the geometry. This can either be a GMTdataset (or vector of it), a Mx2 matrix, the name                         of file that can be read as a GMTdataset by `gmtread()` or a GDAL AbstractDataset object
  * `width`:  - the buffer width to be applied. Expressed meters (the default), km or Miles (see `unit`)
  * `unit`:   - If `width` is not in meters use one of `unit=:km`, or `unit=:Nautical` or `unit=:Miles`
  * `np`:     - Number of points into which circles are descretized (Default = 120)
  * `flatstart` - When computing buffers arround poly-lines make the start *flat* (no half-circle)
  * `flatend`   - Same as `flatstart` but for the buffer end
  * `proj`  - If line data is in Cartesians but with a known projection pass in a PROJ4 string to allow computing the buffer
  * `epsg`  - Same as `proj` but using an EPSG code
  * `tol`   - At the end simplify the buffer line with a Douglas-Peucker procedure. Use TOL=0 to NOT do the line           simplification, or use any other value in degrees. Default computes it as 0.5% of buffer width.

### Returns

A GMT dataset or a vector of it (when input is Vector{GMTdataset})

## Example: Compute a buffer with 50000 m width

```
D = buffergeo([0 0; 10 10; 15 20], width=50000);
```
