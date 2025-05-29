```
@freeze_orbs(freeze_orbs)
```

Freeze orbitals in the integrals according to an array or range    `freeze_orbs`.

Alternatively, the orbitals can be specified as a String with the +/- or :/; syntax, e.g.,   "1-5+7-8", or "1:5;7-8".

# Examples

```julia
fcidump = "FCIDUMP"
@freeze_orbs 1:5
...
@ECinit
@freeze_orbs [1,2,20,21]
```
