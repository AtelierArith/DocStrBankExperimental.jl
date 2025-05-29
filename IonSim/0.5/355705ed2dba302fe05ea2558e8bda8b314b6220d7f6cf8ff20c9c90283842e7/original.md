```
wavelength_from_transition!(laser::Laser, ion, transition::Tuple, chamber::Chamber)
```

Sets the wavelength of `laser` to the transition wavelength of `transition` in the ion `ion`, at the magnetic field seen by `ion` in `chamber`. `ion` may be either an Ion or an Int indicating the desired ion's index within `chamber`.
