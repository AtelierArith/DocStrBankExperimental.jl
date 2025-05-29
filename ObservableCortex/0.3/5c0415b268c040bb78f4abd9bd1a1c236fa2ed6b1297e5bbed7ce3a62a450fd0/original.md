```
axes(m, b)
```

Given a `Montage m`, get a `Vector{Axis3}` listing all axes in the montage that correspond to the given hemisphere `b::BrainStructure` (should be either  `CORTEX_LEFT`, `CORTEX_RIGHT`, or their abbreviations `L` and `R`)
