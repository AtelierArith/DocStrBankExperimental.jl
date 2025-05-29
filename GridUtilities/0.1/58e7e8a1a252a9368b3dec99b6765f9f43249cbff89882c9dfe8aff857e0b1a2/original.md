```
interpolated_history(v::History,xr,yr,tr)
```

Returns a function that interpolates the history `v` both spatially and temporally, using the x and y ranges specified by `xr` and `yr` and time specified by time range `tr`. Uses cubic spline interpolation in all directions. If `v` is a periodic history, then the resulting function is also periodic in time.
