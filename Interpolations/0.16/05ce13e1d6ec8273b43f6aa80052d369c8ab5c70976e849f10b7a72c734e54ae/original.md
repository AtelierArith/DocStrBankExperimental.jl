```
scale(itp, xs, ys, ...)
```

Scales an existing interpolation object to allow for indexing using other coordinate axes than unit ranges, by wrapping the interpolation object and transforming the indices from the provided axes onto unit ranges upon indexing.

The parameters `xs` etc must be either ranges or linspaces, and there must be one coordinate range/linspace for each dimension of the interpolation object.

For every `NoInterp` dimension of the interpolation object, the range must be exactly `1:size(itp, d)`.
