```
window(tns, dims)
```

Create a `WindowedArray` which represents a view into another tensor

```
    window(tns, dims)[i...] == tns[dim[1][i], dim[2][i], ...]
```

The windowed array restricts the new dimension to the dimension of valid indices of each `dim`. The `dims` may also be `nothing` to represent a full view of the underlying dimension.
