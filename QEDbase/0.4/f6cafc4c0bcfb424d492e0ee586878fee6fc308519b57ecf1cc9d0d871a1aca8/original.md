```
getInvariantMass(lv)
```

Return the the invariant mass of a given `LorentzVectorLike`, i.e. the square root of the minkowski dot with itself.

!!! example
    If `(t,x,y,z)` is a `LorentzVectorLike`, this is equivalent to `sqrt(t^2 - (x^2 + y^2 + z^2))`.


!!! note
    If the squared invariant mass `m2` is negative, `-sqrt(-m2)` is returned.

