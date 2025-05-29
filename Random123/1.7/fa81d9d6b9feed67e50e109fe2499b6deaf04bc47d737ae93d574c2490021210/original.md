```julia
ARS1x{R} <: AbstractAESNI1x
ARS1x([seed, R=7])
```

ARS1x is one kind of ARS Counter-Based RNGs. It generates one `UInt128` number at a time.

`seed` is an `Integer` which will be automatically converted to `UInt128`.

`R` denotes to the Rounds which should be at least 1 and no more than 10. With 7 rounds (by default), it has a considerable safety margin over the minimum number of rounds with no known statistical flaws, but still has excellent performance.

Only available when [`R123_USE_AESNI`](@ref).
