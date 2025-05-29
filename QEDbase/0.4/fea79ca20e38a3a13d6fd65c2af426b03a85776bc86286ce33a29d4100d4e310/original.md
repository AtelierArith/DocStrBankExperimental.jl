```
getTheta(lv)
```

Return the theta angle for a given `LorentzVectorLike`, i.e. the polar angle of its spatial components in [spherical coordinates](https://en.wikipedia.org/wiki/Spherical_coordinate_system).

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike` with magnitude `rho`, this is equivalent to `arccos(pz/rho)`, which is also equivalent to `arctan(sqrt(px^2+py^2)/pz)`.


!!! note
    The [spherical coordinates](https://en.wikipedia.org/wiki/Spherical_coordinate_system) are defined w.r.t. to the 3-axis.

