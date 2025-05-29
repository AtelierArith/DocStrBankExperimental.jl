```
Emitter3DFit{T} <: AbstractEmitter
```

Represents fitted 3D localization results with uncertainties and temporal/tracking information.

# Fields

  * `x::T`: fitted x-coordinate in microns
  * `y::T`: fitted y-coordinate in microns
  * `z::T`: fitted z-coordinate in microns
  * `photons::T`: fitted number of photons
  * `bg::T`: fitted background in photons/pixel
  * `σ_x::T`: uncertainty in x position in microns
  * `σ_y::T`: uncertainty in y position in microns
  * `σ_z::T`: uncertainty in z position in microns
  * `σ_photons::T`: uncertainty in photon count
  * `σ_bg::T`: uncertainty in background in photons/pixel
  * `frame::Int`: frame number in acquisition sequence
  * `dataset::Int`: identifier for specific acquisition/dataset
  * `track_id::Int`: identifier for linking localizations across frames (0 = unlinked)
  * `id::Int`: unique identifier within dataset
