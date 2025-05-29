```julia
struct LeftM{T} <: Moonshine.Distance{T}
```

Left marker distance.

This is only the discrete metric for the leftmost marker. Technically not a metric for haplotypes, but widely used.
