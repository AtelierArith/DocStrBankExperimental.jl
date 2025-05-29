```julia
Lookup(uc::UnitCell) --> Dict
```

Returns a dictionary with keys = (base, target, offset) for bond ∈ `UnitCell` bond list, and the entry being the bond matrix.  If there are multiple bonds with the same identifier, it adds them up.
