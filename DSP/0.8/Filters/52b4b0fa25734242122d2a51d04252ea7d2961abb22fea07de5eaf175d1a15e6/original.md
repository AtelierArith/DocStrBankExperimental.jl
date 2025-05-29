```
resample(x::AbstractArray, rate::Real, h::Vector = resample_filter(rate); dims)
resample(x::AbstractArray, rate::AbstractFloat, h::Vector, Nϕ=32; dims)
```

Resample an array `x` along dimension `dims`. If `rate` is an `AbstractFloat`, the number of phases `Nϕ` to be used in constructing `FIRArbitrary` can be supplied as an optional argument, which defaults to 32.
