```
intensity_from_pitime(
    laser::Laser, pi_time::Real, ion::Ion, transition::Tuple,
    Bhat::NamedTuple{(:x,:y,:z)}
)
```

特定の共鳴する `laser`-`ion` の `transition` に対して、特定の `pi_time` を得るために必要な強度を計算します。これは、`Bhat` の方向を指す磁場の存在下で行われます。
