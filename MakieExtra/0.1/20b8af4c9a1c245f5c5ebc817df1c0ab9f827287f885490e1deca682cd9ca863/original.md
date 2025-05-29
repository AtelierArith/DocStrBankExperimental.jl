```
multiplot([pos], plts, args...; kwargs...)
```

Make multiple plots with the same data.

Any combination of `plts` that take the same data is supported. Common examples include:

  * `(lines, band)`,
  * `(scatter, rangebars)`,
  * `(scatter, rangebars, rangebars => (;direction=:x))`
