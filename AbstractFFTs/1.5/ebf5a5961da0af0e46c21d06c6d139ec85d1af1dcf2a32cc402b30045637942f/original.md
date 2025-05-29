```
fftshift(x, [dim])
```

Circular-shift along the given dimension of a periodic signal `x` centered at index `1` so it becomes centered at index `N÷2+1`, where `N` is the size of that dimension.

This can be undone with [`ifftshift`](@ref). For even `N` this is equivalent to swapping the first and second halves, so `fftshift` and [`ifftshift`](@ref) are the same.

If `dim` is not given then the signal is shifted along each dimension.

The output of `fftshift` is allocated. If one desires to store the output in a preallocated array, use [`fftshift!`](@ref) instead.
