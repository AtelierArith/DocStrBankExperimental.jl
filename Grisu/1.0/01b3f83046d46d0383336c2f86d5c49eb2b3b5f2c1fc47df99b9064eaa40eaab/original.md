```
(len, point, neg) = Grisu.grisu(v::AbstractFloat, mode, requested_digits, [buffer], [bignums])
```

Convert the number `v` to decimal using the Grisu algorithm.

`mode` can be one of:

  * `Grisu.SHORTEST`: convert to the shortest decimal representation which can be "round-tripped" back to `v`.
  * `Grisu.FIXED`: round to `requested_digits` digits.
  * `Grisu.PRECISION`: round to `requested_digits` significant digits.

The characters are written as bytes to `buffer`, with a terminating NUL byte, and `bignums` are used internally as part of the correction step. You can call `Grisu.getbuf()` to obtain a suitable task-local buffer.

The returned tuple contains:

  * `len`: the number of digits written to `buffer` (excluding NUL)
  * `point`: the location of the radix point relative to the start of the array (e.g. if `point == 3`, then the radix point should be inserted between the 3rd and 4th digit). Note that this can be negative (for very small values), or greater than `len` (for very large values).
  * `neg`: the signbit of `v` (see [`signbit`](@ref)).
