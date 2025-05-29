```
meander!(p::Path, len, straightlen, r, α)
```

Alternate between going straight with length `straightlen` and turning with radius `r` and angle `α`. Each turn goes the opposite direction of the previous. The total length is `len`. Useful for making resonators.

The straight and turn segments are combined into a `CompoundSegment` and appended to the path `p`.
