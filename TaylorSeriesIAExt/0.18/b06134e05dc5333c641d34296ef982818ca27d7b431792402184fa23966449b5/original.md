```
normalize_taylor(a::TaylorN, I::IntervalBox, symI::Bool=true)
```

Normalize `a::TaylorN` such that the intervals in `I::IntervalBox` are mapped by an affine transformation to the intervals `-1..1` (`symI=true`) or to `0..1` (`symI=false`).
