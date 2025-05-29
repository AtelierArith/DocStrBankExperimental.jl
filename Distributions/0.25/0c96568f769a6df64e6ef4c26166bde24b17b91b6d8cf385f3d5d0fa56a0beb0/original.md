```
pdf(d::Distribution{ArrayLikeVariate{N}}, x::AbstractArray{<:Real,N}) where {N}
```

Evaluate the probability density function of `d` at `x`.

This function checks if the size of `x` is compatible with distribution `d`. This check can be disabled by using `@inbounds`.

# Implementation

Instead of `pdf` one should implement `_pdf(d, x)` which does not have to check the size of `x`. However, since the default definition of `pdf(d, x)` falls back to `logpdf(d, x)` usually it is sufficient to implement `logpdf`.

See also: [`logpdf`](@ref).
