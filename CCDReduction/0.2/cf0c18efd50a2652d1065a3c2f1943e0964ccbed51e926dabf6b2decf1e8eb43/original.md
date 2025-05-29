```
trimview(frame, idxs)
```

Trims the `frame` to remove the region specified by idxs.

This function is same as the [`trim`](@ref) function but returns a view of the frame.

!!! note
    This function returns a view of the frame, so any modification to output array will result in modification of frame.


# See Also

[`trim`](@ref)
