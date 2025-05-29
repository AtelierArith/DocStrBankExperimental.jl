```
intensity_from_rabifrequency(
    laser::Laser, rabi_frequency::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
```

Compute the intensity needed to get a certain `rabi_frequency` with a certain resonant `laser`-`ion` `transition`, in the presence of a magnetic field pointing in the direction `Bhat`.
