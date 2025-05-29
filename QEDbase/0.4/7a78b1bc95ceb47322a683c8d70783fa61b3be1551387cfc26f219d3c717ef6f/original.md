```
getTransverseMass(lv)
```

Return the transverse momentum for a given `LorentzVectorLike`, i.e. the square root of its squared transverse mass.

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `sqrt(E^2 - pz^2)`.


!!! note
    The transverse components are defined w.r.t. to the 3-axis.


!!! note
    If the squared transverse mass `mT2` is negative, `-sqrt(-mT2)` is returned.

