```
shiftedkernel = centered(kernel)
```

Shift the origin-of-coordinates to the center of `kernel`. The center-element of `kernel` will be accessed by `shiftedkernel[0, 0, ...]`.

This function makes it easy to supply kernels using regular Arrays, and provides compatibility with other languages that do not support arbitrary axes.

See also: [`imfilter`](@ref).
