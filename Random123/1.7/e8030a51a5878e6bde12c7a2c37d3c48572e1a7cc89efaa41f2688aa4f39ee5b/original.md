```julia
Philox2x{T, R} <: R123Generator2x{T}
Philox2x([seed, R])
Philox2x(T[, seed, R])
```

Philox2x is one kind of Philox Counter-Based RNGs. It generates two numbers at a time.

`T` is `UInt32` or `UInt64`(default).

`seed` is an `Integer` which will be automatically converted to `T`.

`R` denotes to the Rounds which must be at least 1 and no more than 16. With 10 rounds (by default), it has a considerable safety margin over the minimum number of rounds with no known statistical flaws, but still has excellent performance.
