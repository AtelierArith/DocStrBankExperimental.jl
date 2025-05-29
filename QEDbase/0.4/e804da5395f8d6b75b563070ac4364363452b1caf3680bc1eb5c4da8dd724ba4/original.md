```
getMagnitude2(lv)
```

Return the square of the magnitude of a given `LorentzVectorLike`, i.e. the sum of the squared spatial components.

!!! example
    If `(t,x,y,z)` is a `LorentzVectorLike`, this is equivalent to `x^2+ y^2 + z^2`.


!!! warning
    This function differs from a similar function for the `TLorentzVector` used in the famous `ROOT` library.

