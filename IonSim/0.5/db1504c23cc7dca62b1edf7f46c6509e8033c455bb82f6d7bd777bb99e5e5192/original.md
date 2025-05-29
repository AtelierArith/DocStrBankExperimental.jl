```
intensity_from_rabifrequency!(
    laser::Laser, rabi_frequency::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
intensity_from_rabifrequency!(
    laser, rabi_frequency::Real, ion, transition::Tuple, chamber::Chamber
)
```

Same as `intensity_from_rabifrequency!`, but updates `laser[:I]` in-place.
