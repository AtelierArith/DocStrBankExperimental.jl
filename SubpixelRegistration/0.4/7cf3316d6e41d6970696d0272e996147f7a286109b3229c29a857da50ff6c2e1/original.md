```
phase_offset(source, target; upsample_factor=1, normalize=false)
```

Return the shift between `source` and `target` along each axis by measuring the maximum in the cross-correlation between the images. This algorithm can achieve `1/upsample_factor` precision by locally upsampling the cross-correlation via a matrix-multiplication DFT.[^1] If `normalize` is `true`, the phase of the cross-correlation in Fourier space is divided by its magnitude. In some applications, phase normalization can increase performance, but usually at a trade-off for worse low-noise performance.

# Examples

```jldoctest
julia> image = reshape(1.0:100.0, 10, 10);

julia> shift = (-1.6, 2.8)
(-1.6, 2.8)

julia> target = fourier_shift(image, shift);

julia> phase_offset(image, target)
(shift = (2.0, -3.0), error = 0.013095117382042387, phasediff = 0.0)

julia> phase_offset(image, target; upsample_factor=5)
(shift = (1.6, -2.8), error = -9972.926257260056, phasediff = 0.0)

julia> phase_offset(image, target; upsample_factor=5, normalize=true)
(shift = (1.8, -2.8), error = 0.9999999971143979, phasediff = 0.0)

julia> @. isapprox(ans.shift, -1 * shift, atol=1/5)
(true, true)
```

[^1]: Manuel Guizar-Sicairos, Samuel T. Thurman, and James R. Fienup, ["Efficient subpixel image registration algorithms,"](http://www.opticsinfobase.org/ol/fulltext.cfm?uri=ol-33-2-156&id=148843) Opt. Lett. 33, 156-158 (2008)
