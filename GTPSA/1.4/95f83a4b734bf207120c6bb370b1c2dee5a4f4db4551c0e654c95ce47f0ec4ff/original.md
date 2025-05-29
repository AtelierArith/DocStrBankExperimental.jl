```
@params(descriptor [,complex=bool] [, dynamic=bool])
```

Constructs a vector of `TPS`s corresponding to each of the parameters in the GTPSA `descriptor`

# Keyword Arguments

  * `complex` – If `true`, returns the parameters as `ComplexTPS64`s. Default is `false`.
  * `dynamic` – If `true`, the parameters will use dynamic `Descriptor` resolution. Default is `false`.
