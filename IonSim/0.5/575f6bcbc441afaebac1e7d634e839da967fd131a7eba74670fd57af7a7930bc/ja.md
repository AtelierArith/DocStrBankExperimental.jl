```
intensity_from_pitime(
    laser, pi_time::Real, ion, transition::Tuple, chamber::Chamber
    )
```

特定の `pi_time` を得るために必要な強度を計算します。これは特定の共鳴 `laser`-`ion` `transition` において、磁場の方向を定義する `chamber` 内で行われます。`laser` は、`chamber` 内の希望するレーザーのインデックスを示す Laser または Int のいずれかである可能性があります。`ion` は、`chamber` 内の希望するイオンのインデックスを示す Ion または Int のいずれかである可能性があります。
