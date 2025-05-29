```
isbasemeasureconstant(something)
```

Returns either `NonConstantBaseMeasure()` or `ConstantBaseMeasure()` depending on if the base measure is a constant with respect to the natural parameters of `something` or not. By default the package assumes that any base measure in a form of the `Function` is not a constant. It, however, is not true for basemeasure that simply return a constant. In such cases the `isbasemeasureconstant` must have a specific method.

See also: [`getbasemeasure`](@ref), [`basemeasure`](@ref)
