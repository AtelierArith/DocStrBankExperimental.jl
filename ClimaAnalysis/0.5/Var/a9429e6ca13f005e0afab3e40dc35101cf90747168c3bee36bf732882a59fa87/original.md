```
is_z_1D(var::OutputVar)
```

Return whether the given `var`iable has an altitude dimension that is 1D.

When topography is present, the altitude dimension in the output variable is typically multidimensional. The dimensions are (X, Y, Z), where (X, Y) are the horizontal dimensions. In this case, `dims["z"]` is essentially a map that identifies the physical altitude of the given point.
