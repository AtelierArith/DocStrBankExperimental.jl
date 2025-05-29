```
DimPoints <: AbstractArray

DimPoints(x; order)
DimPoints(dims::Tuple; order)
DimPoints(dims::Dimension; order)
```

Like `CartesianIndices`, but for the point values of the dimension index.  Behaves as an `Array` of `Tuple` lookup values (whatever they are) for all combinations of the lookup values of `dims`.

Either a `Dimension`, a `Tuple` of `Dimension` or an object that defines a `dims` method can be passed in.

# Keywords

  * `order`: determines the order of the points, the same as the order of `dims` by default.
