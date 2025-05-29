```julia
Philox4x{T, R} <: R123Generator4x{T}
Philox4x([seed, R])
Philox4x(T[, seed, R])
```

Philox4x is one kind of Philox Counter-Based RNGs. It generates four numbers at a time.

`T` is `UInt32` or `UInt64`(default).

`seed` is a `Tuple` of two `Integer`s which will both be automatically converted to `T`.

`R` denotes to the Rounds which must be at least 1 and no more than 16. With 10 rounds (by default), it has a considerable safety margin over the minimum number of rounds with no known statistical flaws, but still has excellent performance.
