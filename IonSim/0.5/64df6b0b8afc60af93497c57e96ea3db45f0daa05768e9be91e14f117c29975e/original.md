```
intensity_from_pitime(
    laser::Laser, pi_time::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
```

Compute the intensity needed to get a certain `pi_time` with a certain resonant `laser`-`ion` `transition`, in the presence of a magnetic field pointing in the direction `Bhat`.
