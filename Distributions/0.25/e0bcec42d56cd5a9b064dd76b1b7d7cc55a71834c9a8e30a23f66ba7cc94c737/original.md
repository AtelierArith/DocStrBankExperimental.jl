```
logpdf(d::Distribution{ArrayLikeVariate{N}}, x::AbstractArray{<:Real,N}) where {N}
```

Evaluate the logarithm of the probability density function of `d` at `x`.

This function checks if the size of `x` is compatible with distribution `d`. This check can be disabled by using `@inbounds`.

# Implementation

Instead of `logpdf` one should implement `_logpdf(d, x)` which does not have to check the size of `x`.

See also: [`pdf`](@ref), [`gradlogpdf`](@ref).
