```
CtGeom{Td,To,Ts}
```

Abstract type for representing ray geometries for 3D CT imaging.

The projection view coordinates are `(s,t)` where `s` denotes the transaxial sampling and `t` denotes the axial direction (along `z`).

# Common fields

  * `ns` size of each projection view
  * `nt`
  * `ds` detector pixel spacing
  * `dt`
  * `offset_s` unitless detector center offset (usually 0 or 0.25)
  * `offset_t` unitless, usually 0
  * `na` # of projection views, aka nϕ or nβ
  * `orbit` source orbit in degrees (or Unitful)
  * `orbit_start` starting angle in degrees (or Unitful) `orbit` and `orbit_start` must both be unitless (degrees) or have same units.
  * `src::CtSource` describes the X-ray CT source trajectory. Primary support for `CtSourceCircle()`.

# Additional fields for `CtFan` types:

  * `dsd` distance from source to detector
  * `dod` distance from origin to detector
  * `source_offset` usually 0

# Units:

  * `ds`, `dt`, `source_offset`, `dsd`, `dod` must all be unitless or have the same units.

# Basic methods

  * `angles` (na) in degrees
  * `dims (ns, nt, na)`
  * `ones = ones(Float32, ns,nt,na)`
  * `zeros = zeros(Float32, ns,nt,na)`
  * `rays` iterator of `(u,v,ϕ,θ)` samples
  * `downsample(st, down)` reduce sampling by integer factor
  * `oversample(st, over)`
  * `ct_geom_plot3` plot system geometry

# Non-exported helper functions for developers:

  * `_s (ns) s` sample locations
  * `_t (nt) t` sample locations
  * `_ws = (ns-1)/2 + offset_s` "middle" sample position
  * `_wt = (nt-1)/2 + offset_t`
  * `_ar (na)` source angles [radians]
  * `_rfov` max radius within FOV
  * `_zfov` axial FOV
  * `_xds (nb)` center of detector elements (beta=0)
  * `_yds (nb)` ""
  * `_tau(rg, x, y)` projected s/ds for each `(x,y)` pair `(length(x), na)`
  * `_shape(rg, proj [,:])` reshape `proj` into array `(ns,nt,na[,:])`
  * `_unitv(rg [, (is,it,ia)])` unit 'vector' with single nonzero element

For fan beam:

  * `_dso = dsd - dod` distance from source to origin (Inf for parallel beam)
  * `_dfs` distance from source to detector focal spot       (0 for 3rd gen CT, `Inf` for flat detectors)
  * `_gamma(rg [,s]) (ns)` gamma sample values `radians`, optionally given `s` values
  * `_gamma_max = max(|γ|)` half of fan angle `radians`, if `offset_s` == 0
  * `_cone_angle` (half) cone angle on axis (s=0): +/- angle

# Notes

Use `sino_geom()` instead for 2D geometries.
