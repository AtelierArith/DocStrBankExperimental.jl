```
signal = getFlattenedSignal(signalTable, name;
                            missingToNaN = true,
                            targetInt    = Int,
                            targetFloat  = Float64)
```

Returns a copy of a signal where the *flattened* and *converted* values (e.g.: missing -> NaN) are stored as `signal[:flattenedValues]` and the legend as `signal[:legend]`. A flattened signal can be, for example, used for traditional plot functions or for traditional tables.

`signal[:flattenedValues]` is a reshape of values into a vector or a matrix with optionally the following transformations:

  * `name` can be a signal name with or without array range indices (for example `name = "a.b.c[2,3:5]"`).
  * If `missingToNaN=true`, then missing values are replaced by NaN values. If NaN does not exist in the corresponding type, the values are first converted to `targetFloat`.
  * If targetInt is not nothing, Int-types are converted to targetInt
  * If targetFloat is not nothing, Float-types are converted to targetFloat
  * collect(..) is performed on the result.

`flattenedSignal[:legend]` is a vector of strings that provides a description for every array column (e.g. if `"name=a.b.c[2,3:5]", unit="m/s"`, then `legend = ["a.b.c[2,3] [m/s]", "a.b.c[2,3] [m/s]", "a.b.c[2,5] [m/s]"]`.

If the required transformation is not possible, a warning message is printed and `nothing` is returned.

As a special case, if signal[:values] is a vector or signal[:value] is a scalar and an element of values or value is of type `Measurements{targetFloat}` or `MonteCarloMeasurements{targetFloat}`, then the signal is not transformed, so signal[:flattenedValues] = signal[:values].
