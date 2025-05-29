```
panzoom(x, y[, s = 0])
```

Pan/zoom the axes of the current plot.

The focus of the zoom is set at a point with an offset of `(x, y)` units in normalized device coordinates (NDC) from the center of the current axes. The corners of the axes are linearly displaced towards that point, such that the size of the new axes is `s` times their original size.

If `s` is set to 0 (the default value), the center of the axes is displaced at the focus, without resizing-

# Example

```julia
# Move the center 1 unit right and 0.2 up (NDC)
panzoom(1, 0.2)
# Reduce the focus of the axes to half their size
# focusing on the previous point
panzoom(1, 0.2, 0.5)
```
