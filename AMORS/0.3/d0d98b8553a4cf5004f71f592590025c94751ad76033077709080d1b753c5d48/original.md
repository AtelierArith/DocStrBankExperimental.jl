```
AMORS.solve(f, x0, y0) -> (status, x, y)
```

Apply AMORS strategy out-of-place, that is leaving the initial variables `x0` and `y0` unchanged. See [`AMORS.solve!`](@ref) for a description of the method.

Methods `Base.similar` and `Base.copyto!` must be applicable to objects of same types as `x0` and `y0`.
