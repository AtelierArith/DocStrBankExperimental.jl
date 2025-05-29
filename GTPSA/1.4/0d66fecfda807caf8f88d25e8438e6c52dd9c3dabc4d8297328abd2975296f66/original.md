```
@vars(descriptor [,complex=bool] [, dynamic=bool])
```

Constructs a vector of `TPS`s corresponding to each of the variables in the GTPSA `descriptor`

# Keyword Arguments

  * `complex` – If `true`, returns the variables as `ComplexTPS64`s. Default is `false`.
  * `dynamic` – If `true`, the variables will use dynamic `Descriptor` resolution. Default is `false`.
