```
DipoleEmitter3D{T} <: AbstractEmitter
```

3D dipole emitter with position, orientation and optical properties.

# Fields

  * `x::T`: x-coordinate in microns
  * `y::T`: y-coordinate in microns
  * `z::T`: z-coordinate in microns
  * `photons::T`: number of photons
  * `dipole::DipoleVector{T}`: dipole orientation vector
