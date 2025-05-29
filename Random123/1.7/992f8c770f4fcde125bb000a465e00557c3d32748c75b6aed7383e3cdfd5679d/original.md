```julia
AESNI4x <: AbstractAESNI4x
AESNI4x([seed])
```

AESNI4x is one kind of AESNI Counter-Based RNGs. It generates four `UInt32` numbers at a time.

`seed` is a `Tuple` of four `Integer`s which will all be automatically converted to `UInt32`.

Only available when [`R123_USE_AESNI`](@ref).
