```
RectVolSurface(reference_date, rate, spot, tenors, strikes, prices; kwargs...)
```

Calibrates a `RectVolSurface` from observed option prices. Handles optional `call_put_matrix` and allows customization of interpolation/extrapolation.
