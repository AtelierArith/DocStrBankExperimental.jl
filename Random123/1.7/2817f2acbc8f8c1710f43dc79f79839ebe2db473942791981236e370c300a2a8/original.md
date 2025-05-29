```julia
Threefry4x{T, R} <: R123Generator4x{T}
Threefry4x([seed, R])
Threefry4x(T[, seed, R])
```

Threefry2x is one kind of Threefry Counter-Based RNGs. It generates four numbers at a time.

`T` is `UInt32` or `UInt64`(default).

`seed` is a `Tuple` of four `Integer`s which will all be automatically converted to `T`.

`R` denotes to the Rounds which must be at least 1 and no more than 32. With 20 rounds (by default), it has a considerable safety margin over the minimum number of rounds with no known statistical flaws, but still has excellent performance.
