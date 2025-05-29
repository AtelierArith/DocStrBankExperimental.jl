```
WeakBoundaries()
```

Allows small overshoots at boundaries, but not large ones. Errors are only triggered when the interpolation coordinate is outside of a boundary and not close to it. At the lower boundary, for example, an error would be triggered when `(x < boundary) & !(x ≈ boundary)`.
