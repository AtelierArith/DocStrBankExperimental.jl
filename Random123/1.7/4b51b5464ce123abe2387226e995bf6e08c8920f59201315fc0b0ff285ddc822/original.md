```julia
ARS4x{R} <: AbstractAESNI4x
ARS4x([seed, R=7])
```

ARS4x is one kind of ARS Counter-Based RNGs. It generates four `UInt32` numbers at a time.

`seed` is a `Tuple` of four `Integer`s which will all be automatically converted to `UInt32`.

`R` denotes to the Rounds which must be at least 1 and no more than 10. With 7 rounds (by default), it has a considerable safety margin over the minimum number of rounds with no known statistical flaws, but still has excellent performance.

Only available when [`R123_USE_AESNI`](@ref).
