```
convert_arguments(::ImageLike, mat::AbstractMatrix)
```

Generates `ClosedInterval`s of size `0 .. size(mat, 1/2)` as x and y values.
