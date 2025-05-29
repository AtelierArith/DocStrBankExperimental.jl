```
symsqueeze(cut::Cut) -> cut2::Cut
```

Squeeze a symmetric cut with ϕ values equally distributed in [0,360) into [0, 180).

The ϕ values must define nonredundant cuts.  I.e., `cut.phi` must be equivalent to the vector `[0, Δϕ, 2Δϕ, 3Δϕ, ..., (360 - Δϕ)]`, with `length(cut.phi)` being an odd number, so that 180 is excluded.

`cut2` will have Δϕ/2 as its ϕ increment, and it's maximum ϕ value will be `180 - Δϕ/2`.
