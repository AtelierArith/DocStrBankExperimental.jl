```
interpolated_history(v::History,tr)
```

Returns a function that interpolates the history `v`, using the time specified by time range `tr`. Uses cubic spline interpolation. If `v` is a periodic history, then the resulting function is also periodic.
