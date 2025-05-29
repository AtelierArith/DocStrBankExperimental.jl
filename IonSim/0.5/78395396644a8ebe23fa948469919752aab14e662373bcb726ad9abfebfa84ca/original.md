```
intensity_from_pitime!(
    laser::Laser, pi_time::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
intensity_from_pitime!(
    laser, pi_time::Real, ion, transition::Tuple, chamber::Chamber
)
```

Same as `intensity_from_pitime`, but updates `laser[:I]` in-place.
