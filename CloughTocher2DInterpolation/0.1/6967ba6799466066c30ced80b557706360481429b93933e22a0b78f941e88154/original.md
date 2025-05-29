```
CloughTocher2DInterpolator(points, values; kwargs...)
```

Setup a Clough-Tocher 2D interpolator for a given cloud of `points` and `values`.

`points` holds the data in "component major order". E.g. a single triangle with points `(0,0), (1,0), (0,1)` is encoded as `points = [ 0,0, 1,0, 0,1 ]`.

Available keyword arguments:

  * fill_value=NaN: Value used to fill in for requested points outside of the convex hull of the input points.
  * tol=1e-6: Tolerance for gradient estimation.
  * maxiter=400: Maximum number of iterations in gradient estimation.
  * rescale=false: Rescale points to unit cube before performing interpolation.  This is useful if some of the input dimensions have incommensurable units and differ by many orders of magnitude.

# Example

```julia
points  = [0,0, 0,1, 1,0, 1,1, 2,0, 2,1]
ipoints = [0.5,0.5, 1.5,0.5]

# real
data   = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
interp = CloughTocher2DInterpolator(points, data)
interp(ipoints)

# complex
data   = [1.0+2.0im, 2.0+3.0im, 3.0-1.0im, 4.0-0.5im, 5.0-3.0im, 6.0+5.0im]
interp = CloughTocher2DInterpolator(points, data)
interp(ipoints)

# interpolate data into preallocated array (will be resized if necessary)
result = zeros(eltype(data), length(data))
interp(ipoints, result)
```
