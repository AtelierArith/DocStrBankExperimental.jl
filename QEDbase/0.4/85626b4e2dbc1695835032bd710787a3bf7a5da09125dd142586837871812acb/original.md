```
getPhi(lv)
```

Return the phi angle for a given `LorentzVectorLike`, i.e. the azimuthal angle of its spatial components in [spherical coordinates](https://en.wikipedia.org/wiki/Spherical_coordinate_system).

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `atan(py,px)`.


!!! note
    The [spherical coordinates](https://en.wikipedia.org/wiki/Spherical_coordinate_system) are defined w.r.t. to the 3-axis.

