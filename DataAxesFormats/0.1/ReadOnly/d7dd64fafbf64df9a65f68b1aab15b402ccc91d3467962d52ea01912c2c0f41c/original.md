```
read_only_array(array::AbstractArray):AbstractArray
```

Return an immutable view of an `array`. This uses `SparseArrays.ReadOnly`, and properly deals with `NamedArray`. If the array is already immutable, it is returned as-is.
