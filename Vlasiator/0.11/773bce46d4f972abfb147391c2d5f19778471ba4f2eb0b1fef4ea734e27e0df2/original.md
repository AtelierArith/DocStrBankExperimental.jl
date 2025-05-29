```
getKLdivergence(meta, VDF; species="proton")
getKLdivergence(meta, vcellids, vcellf; species="proton")
```

Obtain the KL-divergence ∫ f*log(f/g)dv, where `f` is the VDF from Vlasiator and `g` is the analytical Maxwellian distribution that generates the same density as `f`. The value ranges from [0, +∞], with 0 meaning perfect Maxwellian. Usually the values are quite small. Alternatively, one can pass original `vcellids` and `vcellf` directly.
