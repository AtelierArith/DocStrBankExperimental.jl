```
cropview(frame, shape; force_equal = true)
```

Crops `frame` to the size specified by `shape` anchored by the frame center.

This function is same as the [`crop`](@ref) function but returns a view of the frame.

!!! note
    This function returns a view of the frame, so any modification to output array will result in modification of frame.


# See Also

[`crop`](@ref)
