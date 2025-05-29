```
backproject_filtered(sinogram, θs; 
                        geometry, μ, filter)
```

Reconstruct the image from the `sinogram` using the filtered backprojection algorithm.

  * `filter=nothing`: The filter to be applied in Fourier space. If `nothing`, a ramp filter is used. `filter` should be a 1D array of the same length as the sinogram.

See [`radon`](@ref) for the explanation of the keyword arguments
