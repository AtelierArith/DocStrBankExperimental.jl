```
getBeta(lv)
```

Return magnitude of the beta vector for a given `LorentzVectorLike`, i.e. the magnitude of the `LorentzVectorLike` divided by its 0-component.

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `sqrt(px^2 + py^2 + pz^2)/E`.

