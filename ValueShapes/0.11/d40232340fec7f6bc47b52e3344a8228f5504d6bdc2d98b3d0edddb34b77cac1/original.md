```
ConstValueDist <: Distributions.Distribution
```

Represents a delta distribution for a constant value of arbritrary type.

Calling `varshape` on a `ConstValueDist` will yield a [`ConstValueShape`](@ref).
