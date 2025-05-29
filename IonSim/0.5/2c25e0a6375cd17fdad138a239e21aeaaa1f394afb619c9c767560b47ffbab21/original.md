```
bfield(chamber::Chamber, ion)
```

Retuns the value of the magnetic field in `T` at the location of `ion`, including both the trap's overall B-field and its B-field gradient. `ion` may be either an Ion or an Int indicating the desired ion's index within `chamber`.
