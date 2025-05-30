```
mask_from_voxelquality(qmap::AbstractArray, threshold=:auto)
```

Creates a mask from a quality map. Another option is to use `robustmask(qmap)`

# Examples

```julia-repl
julia> qmap = romeovoxelquality(phase_3echo; TEs=[1,2,3]);
julia> mask = mask_from_voxelquality(qmap);
```

See also [`robustmask`](@ref), [`brain_mask`](@ref)
