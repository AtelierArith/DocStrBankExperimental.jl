```
findlocalmaxima(img; window=default_window(img), edges=true) -> Vector{CartesianIndex}
```

Returns the coordinates of elements whose value is larger than all of their immediate neighbors. `edges` is a Boolean specifying whether to include the first and last elements of each dimension, or a tuple-of-Bool specifying edge behavior for each dimension separately.

The `default_window` is 3 for each spatial dimension of `img`, and 1 otherwise, implying that maxima are detected over nearest-neighbors in each spatial "slice" by default.
