```
coregister(cube; dims, refidx=firstindex(cube, dims), upsample_factor=1)
```

Coregister a cube of data along `dims`, using the `refidx` slice as the source frame. Other keyword arguments will be passed to [`phase_offset`](@ref)

# See also

[`coregister!`](@ref)
