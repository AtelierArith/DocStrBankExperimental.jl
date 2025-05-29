```
getTransverseMass2(lv)
```

Return the squared transverse mass for a given `LorentzVectorLike`, i.e. the difference of its squared 0- and 3-component.

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `E^2 - pz^2`.


!!! note
    The transverse components are defined w.r.t. to the 3-axis.

