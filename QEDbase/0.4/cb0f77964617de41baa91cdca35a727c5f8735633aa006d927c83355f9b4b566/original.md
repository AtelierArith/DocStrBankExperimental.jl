```
getTransverseMomentum(lv)
```

Return the transverse momentum for a given `LorentzVectorLike`, i.e. the magnitude of its transverse components.

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `sqrt(px^2 + py^2)`.


!!! note
    The transverse components are defined w.r.t. to the 3-axis.

