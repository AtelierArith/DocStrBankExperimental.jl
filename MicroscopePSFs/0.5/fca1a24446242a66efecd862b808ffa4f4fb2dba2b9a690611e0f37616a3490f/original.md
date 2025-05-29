```
DipoleEmitter3D(x::Real, y::Real, z::Real, photons::Real,
                dx::Real, dy::Real, dz::Real)
```

Create a `DipoleEmitter3D` with specified position, number of photons, and dipole orientation. The dipole orientation vector will be normalized.

# Arguments

  * `x::Real`: x-coordinate in microns
  * `y::Real`: y-coordinate in microns
  * `z::Real`: z-coordinate in microns
  * `photons::Real`: number of photons
  * `dx::Real`: x component of dipole orientation (normalized)
  * `dy::Real`: y component of dipole orientation (normalized)
  * `dz::Real`: z component of dipole orientation (normalized)
