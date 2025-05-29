```
register(source, target; upsample_factor=1)
```

Register `target` image to `source` image by first finding the phase offset ([`phase_offset`](@ref)), and then Fourier shifting `target` with [`fourier_shift`](@ref).

# Examples

```jldoctest
julia> image = reshape(1.0:100.0, 10, 10);

julia> shift = (-1.6, 2.8)
(-1.6, 2.8)

julia> target = fourier_shift(image, shift);

julia> target_shift = register(image, target; upsample_factor=5);
```

# See also

[`phase_offset`](@ref)
