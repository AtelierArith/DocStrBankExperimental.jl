```
from_float_array(A)
```

Reinterpret a float array as an array of quaternions

The input array must have an initial dimension whose size is 4, because successive indices in that dimension will be considered successive components of the output quaternion.

Note that this returns a view of the original data [via `reinterpret(reshape,...)`] only if the base type of the input array `isbitstype`; otherwise, a new array of `Quaternion`s must be created, and the memory copied.

See also [`to_float_array`](@ref).
