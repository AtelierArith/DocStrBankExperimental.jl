```
getMinus(lv)
```

Return the minus component for a given `LorentzVectorLike` in [light-cone coordinates](https://en.wikipedia.org/wiki/Light-cone_coordinates).

!!! example
    If `(E,px,py,pz)` is a `LorentzVectorLike`, this is equivalent to `(E-pz)/2`.


!!! note
    The [light-cone coordinates](https://en.wikipedia.org/wiki/Light-cone_coordinates) are defined w.r.t. to the 3-axis.


!!! warning
    The definition ``p^- := (E - p_z)/2` differs from the usual definition of [light-cone coordinates](https://en.wikipedia.org/wiki/Light-cone_coordinates) in general relativity.

