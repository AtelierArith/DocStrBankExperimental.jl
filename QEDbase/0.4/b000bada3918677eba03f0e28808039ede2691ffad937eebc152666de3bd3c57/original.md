```
getMagnitude(lv)
```

Return the magnitude of a given `LorentzVectorLike`, i.e. the euklidian norm spatial components.

!!! example
    If `(t,x,y,z)` is a `LorentzVectorLike`, this is equivalent to `sqrt(x^2 + y^2 + z^2)`.


!!! warning
    This function differs from a similar function for the `TLorentzVector` used in the famous `ROOT` library.

