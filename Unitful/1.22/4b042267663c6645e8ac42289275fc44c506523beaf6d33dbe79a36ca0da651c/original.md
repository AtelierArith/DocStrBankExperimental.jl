```
uconvertp(u::Units, x)
uconvertp(u::MixedUnits, x)
```

Generically, this is the same as [`Unitful.uconvert`](@ref). In cases where unit conversion would be ambiguous without further information (e.g. `uconvert(dB, 10)`), `uconvertp` presumes ratios are of power quantities.

It is important to note that careless use of this function can lead to erroneous calculations. Consider `Quantity{<:Gain}` types: it is tempting to use this to transform `-20dB/m` into `0.1/m`, however this means something fundamentally different than `-20dB/m`. Consider what happens when you try to compute exponential attenuation by multiplying `0.1/m` by a length.

Examples:

```jldoctest
julia> using Unitful

julia> uconvertp(u"dB", 10)
10.0 dB

julia> uconvertp(NoUnits, 20u"dB")
100.0
```
