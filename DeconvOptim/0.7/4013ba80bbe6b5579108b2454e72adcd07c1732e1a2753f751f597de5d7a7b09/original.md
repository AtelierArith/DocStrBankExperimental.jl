```
generate_psf(psf_size, radius)
```

Generation of an approximate 2D PSF. `psf_size` is the output size of the PSF. The PSF will be centered around the point [1, 1], `radius` indicates the pupil diameter in pixel from which the PSF is generated.

!!! note
    Returned 2D PSF is `fftshift`ed in contrast to models, you can find in  literature.


# Examples

```julia-repl
julia> generate_psf([5, 5], 2)
5×5 Array{Float64,2}:
 0.36       0.104721    0.0152786    0.0152786    0.104721
 0.104721   0.0304627   0.00444444   0.00444444   0.0304627
 0.0152786  0.00444444  0.000648436  0.000648436  0.00444444
 0.0152786  0.00444444  0.000648436  0.000648436  0.00444444
 0.104721   0.0304627   0.00444444   0.00444444   0.0304627
```
