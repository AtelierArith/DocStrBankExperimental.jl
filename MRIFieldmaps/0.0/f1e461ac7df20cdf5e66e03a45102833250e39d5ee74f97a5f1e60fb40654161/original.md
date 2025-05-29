```
zdata, sos = coil_combine(ydata [, smap])
```

For estimating a B0 field map from complete multi-coil image data, it suffices to first do complex coil combination, while tracking the sum-of-squares `sos` for proper weighting. When sensitivity maps are provided, often `sos` is all 1's and 0's.

Uses a phase contrast coil combination approach (reference below) when sensitivity maps are not provided.

# In

  * `ydata (dims..., nc, ne)` `ne ≥ 1` sets of complex images for `nc ≥ 1` coils
  * `smap (dims..., nc)` complex coil maps (optional)

# Out

  * `zdata (dims..., ne)` complex coil combination: `sum_c smap[c]' * ydata[c] ./ sos` or `sum_c ydata[c,1]' * ydata[c] ./ sos` (if `smap` not provided or `isnothing(smap)`)
  * `sos (dims...)` sum-of-squares: `sum_c |smap[c]|^2` or `sqrt.(sum_c |ydata[c,1]|^2` (if `smap` not provided or `isnothing(smap)`)

See equation [13] in M A Bernstein et al., "Reconstructions of Phase Contrast, Phased Array Multicoil Data", MRM 1994. https://doi.org/10.1002/mrm.1910320308
