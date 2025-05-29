```julia
AESNI1x <: AbstractAESNI1x
AESNI1x([seed])
```

AESNI1x is one kind of AESNI Counter-Based RNGs. It generates one `UInt128` number at a time.

`seed` is an `Integer` which will be automatically converted to `UInt128`.

Only available when [`R123_USE_AESNI`](@ref).
