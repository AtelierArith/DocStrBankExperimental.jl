```
SinoGeom{Td,To}
```

Abstract type for representing ray geometries for 2D sinograms. This describes the sampling characteristics of a given sinogram for a 2D parallel or fan-beam system.

# Common fields

  * `nb` # of "radial" samples, aka `nr` or `ns`
  * `d` aka `dr` or `ds`, "radial" sample spacing
  * `offset` unitless sample offset (usually 0 or 0.25)
  * `na` # of angular samples, aka `nϕ` or `nβ`  default: `2 * floor(Int, nb * π/2 / 2)`
  * `orbit` source orbit in degrees (or Unitful)
  * `orbit_start` starting angle in degrees (or Unitful) `orbit` and `orbit_start` must both be unitless (degrees) or have same units.

# Additional fields for `SinoFan` types

  * `dsd` distance from source to detector
  * `dod` distance from origin to detector
  * `source_offset` usually 0

# Units:

  * `d`, `source_offset`, `dsd`, `dod` must all have the same units.

# Basic methods

  * `angles` (na) in degrees
  * `dims (nb, na)`
  * `ones = ones(Float32, nb, na)`
  * `zeros = zeros(Float32, nb, na)`
  * `rays` iterator of `(r, ϕ)` parallel-beam coordinate tuples of size `(nb, na)`
  * `downsample(st, down)` reduce sampling by integer factor
  * `oversample(st, over)`
  * `sino_geom_plot!` plot system geometry

# Non-exported helper functions for developers:

  * `_ds|dr` radial sample spacing (`NaN` for `:moj`)
  * `_s (nb) s` sample locations
  * `_w = (nb-1)/2 + offset` "middle" sample position
  * `_ar (na)` source angles [radians]
  * `_rfov` radial FOV
  * `_xds (nb)` center of detector elements (beta=0)
  * `_yds (nb)` ""
  * `_tau(rg, x, y)` projected s/ds for each `(x,y)` pair `(length(x), na)`
  * `_shape(rg, sino [,:])` reshape `sino` into array `(nb,na[,:])`
  * `_unitv(rg [, (ib,ia)])` unit 'vector' with single nonzero element

For mojette:

  * `_d_ang (na)` angle-dependent radial spacing

For fan beam:

  * `_dso = dsd - dod` distance from source to origin (Inf for parallel beam)
  * `_dfs` distance from source to detector focal spot       (0 for 3rd gen CT, `Inf` for flat detectors)
  * `_gamma(rg [,s]) (nb)` gamma sample values `radians`, optionally given `s` values
  * `_gamma_max = max(|γ|)` half of fan angle `radians`, if `offset_s` == 0

# Notes

  * Use `ct_geom()` instead for 3D axial or helical cone-beam CT.
