```
to_float_array(A)
```

View a quaternion array as an array of numbers

The output array will have an extra initial dimension whose size is 4, because successive indices in that dimension correspond to successive components of the quaternion.

Note that this returns a view of the original data only if the base type of the input array `isbitstype`; otherwise, a new array of that type must be created, and the memory copied.

See also [`from_float_array`](@ref).
