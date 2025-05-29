```
function set_units(;energy=missing, length=missing, both=missing)
```

Set global units for energy/length. Run with no arguments to check/return current units.

  * Default units are `"eV"` and `"Angstrom"` (or `"Å"` or `"Ang"` ).
  * Choose atomic units by setting `energy="Ryd"` and `length="Bohr"`.
  * Set both at the same time with `both="atomic"` or `both="eVAng"`
  * Internally, all units are atomic. Only main public facing functions actually change units.
