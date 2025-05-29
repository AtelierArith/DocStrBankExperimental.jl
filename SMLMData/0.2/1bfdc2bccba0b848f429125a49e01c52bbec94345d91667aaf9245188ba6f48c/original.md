```
Emitter3DFit{T}(x, y, z, photons, bg, σ_x, σ_y, σ_z, σ_photons, σ_bg;
                frame=0, dataset=1, track_id=0, id=0) where T
```

Convenience constructor for 3D localization fit results with optional identification parameters.

# Arguments

## Required

  * `x::T`: fitted x-coordinate in microns
  * `y::T`: fitted y-coordinate in microns
  * `z::T`: fitted z-coordinate in microns
  * `photons::T`: fitted number of photons
  * `bg::T`: fitted background in photons/pixel
  * `σ_x::T`: uncertainty in x position in microns
  * `σ_y::T`: uncertainty in y position in microns
  * `σ_z::T`: uncertainty in z position in microns
  * `σ_photons::T`: uncertainty in photon count
  * `σ_bg::T`: uncertainty in background level

## Optional Keywords

  * `frame::Int=0`: frame number in acquisition sequence
  * `dataset::Int=1`: identifier for specific acquisition/dataset
  * `track_id::Int=0`: identifier for linking localizations across frames
  * `id::Int=0`: unique identifier within dataset

# Example

```julia
# Create emitter with just required parameters
emitter = Emitter3DFit{Float64}(
    1.0, 2.0, -0.5,  # x, y, z
    1000.0, 10.0,    # photons, background
    0.01, 0.01, 0.02,# σ_x, σ_y, σ_z
    50.0, 2.0        # σ_photons, σ_bg
)

# Create emitter with specific frame and tracking
emitter = Emitter3DFit{Float64}(
    1.0, 2.0, -0.5, 1000.0, 10.0, 0.01, 0.01, 0.02, 50.0, 2.0;
    frame=5, track_id=1
)
```
