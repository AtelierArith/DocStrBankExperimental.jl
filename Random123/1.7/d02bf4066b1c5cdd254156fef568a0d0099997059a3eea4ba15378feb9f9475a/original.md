```julia
Threefry2x{T, R} <: R123Generator2x{T}
Threefry2x([seed, R])
Threefry2x(T[, seed, R])
```

Threefry2x is one kind of Threefry Counter-Based RNGs. It generates two numbers at a time.

`T` is `UInt32` or `UInt64`(default).

`seed` is a `Tuple` of two `Integer`s which will both be automatically converted to `T`.

`R` denotes to the Rounds which must be at least 1 and no more than 32. With 20 rounds (by default), it has a considerable safety margin over the minimum number of rounds with no known statistical flaws, but still has excellent performance.
