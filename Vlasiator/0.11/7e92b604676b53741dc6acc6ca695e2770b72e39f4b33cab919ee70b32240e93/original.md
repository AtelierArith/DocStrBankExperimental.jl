```
getmaxwellianity(meta, VDF; species="proton")
getmaxwellianity(meta, vcellids, vcellf; species="proton")
```

Obtain the Maxwellian similarity factor -log(1/(2n) * ∫ |f - g| dv), where `f` is the VDF from Vlasiator and `g` is the analytical Maxwellian distribution that generates the same density as `f`. The value ranges from [0, +∞], with 0 meaning not Maxwellian-distributed at all, and +∞ a perfect Maxwellian distribution. Alternatively, one can pass original `vcellids` and `vcellf` directly.
