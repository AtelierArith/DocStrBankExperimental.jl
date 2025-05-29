```
normalize_taylor(a::Taylor1, I::Interval, symI::Bool=true)
```

Normalizes `a::Taylor1` such that the interval `I` is mapped by an affine transformation to the interval `-1..1` (`symI=true`) or to `0..1` (`symI=false`).
