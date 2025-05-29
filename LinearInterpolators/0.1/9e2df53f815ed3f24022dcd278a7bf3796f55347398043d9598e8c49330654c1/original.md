```
TwoDimensionalTransformInterpolator(rows, cols, ker1, ker2, R)
```

yields a linear mapping which interpolates its input of size `cols` to produce an output of size `rows` by 2-dimensional interpolation with kernels `ker1` and `ker2` along each dimension and applying the affine coordinate transform specified by `R`.

As a shortcut:

```
TwoDimensionalTransformInterpolator(rows, cols, ker, R)
```

is equivalent to `TwoDimensionalTransformInterpolator(rows,cols,ker,ker,R)` that is the same kernel is used along all dimensions.
