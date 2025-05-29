```
integrate_pixels_amplitude(
    psf::VectorPSF,
    camera::AbstractCamera,
    emitters::Vector{<:AbstractEmitter};
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF complex amplitude over camera pixels for multiple emitters. Special version for VectorPSF that preserves polarization components.

# Arguments

  * `psf`: VectorPSF instance
  * `camera`: Camera geometry defining pixel edges
  * `emitters`: Vector of emitters with position information
  * `sampling`: Subpixel sampling density (default: 2)
  * `threaded`: Whether to use multi-threading for integration (default: true)

# Returns

  * 3D array of integrated complex amplitudes with dimensions [y, x, pol] where pol index 1 = Ex and pol index 2 = Ey

# Notes

  * Results are the coherent sum of individual emitter field contributions
