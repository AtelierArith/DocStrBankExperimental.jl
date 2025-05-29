```
integrate_pixels_amplitude(
    psf::VectorPSF,
    camera::AbstractCamera,
    emitter::AbstractEmitter;
    sampling::Integer=2,
    threaded::Bool=true
)
```

Specialized version of amplitude integration for VectorPSF that preserves polarization components.

# Arguments

  * `psf`: VectorPSF instance
  * `camera`: Camera geometry defining pixel edges
  * `emitter`: Emitter with position information
  * `sampling`: Subpixel sampling density (default: 2)
  * `threaded`: Whether to use multi-threading for integration (default: true)

# Returns

  * 3D array of integrated complex amplitudes with dimensions [y, x, pol] where pol index 1 = Ex and pol index 2 = Ey
