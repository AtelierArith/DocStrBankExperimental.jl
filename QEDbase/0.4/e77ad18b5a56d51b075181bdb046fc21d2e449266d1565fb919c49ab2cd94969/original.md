```
getRapidity(lv)
```

Return the [rapidity](https://en.wikipedia.org/wiki/Rapidity) for a given `LorentzVectorLike`.

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `0.5*log((E+pz)/(E-pz))`.


!!! note
    The transverse components are defined w.r.t. to the 3-axis.

