```
robustmask(weight::AbstractArray; factor=1, threshold=nothing)
```

Creates a mask from an intensity/weight images by estimating a threshold and hole filling. It assumes that at least one corner is without signal and only contains noise. The automatic threshold is multiplied with `factor`.

# Examples

```julia-repl
julia> mask1 = robustmask(mag); # Using magnitude
julia> mask2 = phase_based_mask(phase); # Using phase
julia> mask3 = robustmask(romeovoxelquality(phase; mag)); # Using magnitude and phase
julia> brain = brain_mask(robustmask(romeovoxelquality(phase; mag); threshold=0.9));
```

See also [`brain_mask`](@ref)
