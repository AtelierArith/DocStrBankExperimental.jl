```
FixedMemoryPwq(len::Int64)
```

Represents piecewise quadratic function with a fixed-length Vector of `BoundedQuadratic`s.

The fields represent:

  * `f_list`: a `Vector` of `BoundedQuadratic` functions
  * `len`: how many of the `f_list` entries are filled in.
