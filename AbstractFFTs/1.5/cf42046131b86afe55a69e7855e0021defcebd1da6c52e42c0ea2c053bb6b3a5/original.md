```
ifftshift(x, [dim])
```

Circular-shift along the given dimension of a periodic signal `x` centered at index `N÷2+1` so it becomes centered at index `1`, where `N` is the size of that dimension.

This undoes the effect of [`fftshift`](@ref). For even `N` this is equivalent to swapping the first and second halves, so [`fftshift`](@ref) and `ifftshift` are the same.

If `dim` is not given then the signal is shifted along each dimension.

The output of `ifftshift` is allocated. If one desires to store the output in a preallocated array, use [`ifftshift!`](@ref) instead.
