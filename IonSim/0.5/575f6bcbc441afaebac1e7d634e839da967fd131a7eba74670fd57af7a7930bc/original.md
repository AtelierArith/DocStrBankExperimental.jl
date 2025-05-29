```
intensity_from_pitime(
    laser, pi_time::Real, ion, transition::Tuple, chamber::Chamber
    )
```

Compute the intensity needed to get a certain `pi_time` with a certain resonant `laser`-`ion` `transition` within `chamber`, which defines the magnetic field direction. `laser` may be either a Laser or an Int indicating the desired laser's index within `chamber`. `ion` may be either an Ion or an Int indicating the desired ion's index within `chamber`.
