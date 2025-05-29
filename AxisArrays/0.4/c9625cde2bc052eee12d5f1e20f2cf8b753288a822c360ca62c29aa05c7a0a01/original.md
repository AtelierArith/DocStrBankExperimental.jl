```
axes(A::AxisArray) -> (Axis...)
axes(A::AxisArray, ax::Axis) -> Axis
axes(A::AxisArray, dim::Int) -> Axis
```

Returns the tuple of axis vectors for an AxisArray. If an specific `Axis` is specified, then only that axis vector is returned.  Note that when extracting a single axis vector, `axes(A, Axis{1})`) is type-stable and will perform better than `axes(A)[1]`.

For an AbstractArray without `Axis` information, `axes` returns the default axes, i.e., those that would be produced by `AxisArray(A)`.
