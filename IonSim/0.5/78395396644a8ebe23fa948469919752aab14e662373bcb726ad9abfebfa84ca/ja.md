```
intensity_from_pitime!(
    laser::Laser, pi_time::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
intensity_from_pitime!(
    laser, pi_time::Real, ion, transition::Tuple, chamber::Chamber
)
```

`intensity_from_pitime`と同様ですが、`laser[:I]`をインプレースで更新します。
