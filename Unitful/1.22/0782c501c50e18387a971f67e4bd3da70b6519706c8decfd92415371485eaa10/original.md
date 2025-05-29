```
uconvertrp(u::Units, x)
uconvertrp(u::MixedUnits, x)
```

In most cases, this is the same as [`Unitful.uconvert`](@ref). In cases where unit conversion would be ambiguous without further information (e.g. `uconvert(dB, 10)`), `uconvertrp` presumes ratios are of root-power quantities.

It is important to note that careless use of this function can lead to erroneous calculations. Consider `Quantity{<:Gain}` types: it is tempting to use this to transform `-20dB/m` into `0.01/m`, however this means something fundamentally different than `-20dB/m`. Consider what happens when you try to compute exponential attenuation by multiplying `0.01/m` by a length.
