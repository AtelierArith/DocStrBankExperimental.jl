```julia
function taperinfo(taper::Taper)
```

Return the name of the tapering window(s) encapsulated in the [Taper](@ref) object as a string.

Only for Slepian's discrete prolate spheroidal sequences (dpss), their parameters, namely, $α$ (half-bandwidth) and $n$ (number of windows), are reported within parentheses as well.

**Examples**:

```julia
H=taper(hamming, 128*8)
taperinfo(H)

H=slepians(128, 128*8, 2)
taperinfo(H)
```
