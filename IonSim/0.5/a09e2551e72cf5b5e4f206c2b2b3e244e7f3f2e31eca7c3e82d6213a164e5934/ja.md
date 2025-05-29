```
intensity_from_rabifrequency(
    laser::Laser, rabi_frequency::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
```

特定の共鳴する `laser`-`ion` の `transition` に対して、特定の `rabi_frequency` を得るために必要な強度を計算します。これは、方向 `Bhat` に向かう磁場の存在下で行われます。
