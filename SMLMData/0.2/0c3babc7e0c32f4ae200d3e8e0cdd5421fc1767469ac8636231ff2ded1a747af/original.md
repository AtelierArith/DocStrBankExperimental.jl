```
Emitter3D{T} <: AbstractEmitter
```

Represents a 3D emitter for SMLM simulations with position and brightness.

# Fields

  * `x::T`: x-coordinate in microns
  * `y::T`: y-coordinate in microns
  * `z::T`: z-coordinate in microns (axial position)
  * `photons::T`: number of photons emitted by the fluorophore
