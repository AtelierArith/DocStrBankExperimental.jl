```
packing_fraction(wm::BitArray)
```

Evaluate the packing fraction in a walkmap `wm`.

If `wm` was generated with `probe_radius=0` this represents the real packing fraction, instead if `probe_radius` was not zero, it represents the effective packing fraction experienced by the probe.

Unlike the other instances of `packing_fraction`, this one is exact, independently of overlaps and boundary conditions, within the resolution of the walkmap.
