```
struct PolynomialDNI <: DNIMethod
```

Polynomial denoising and interpolation method.

Operates in a similar way as a [Savitzky-Golay filter](https://en.wikipedia.org/wiki/Savitzky%E2%80%93Golay_filter), but interpolates as well.

Constructors:

  * `PolynomialDNI(; fields...)`

Fields:

  * `degree::Int64`: polynomial degree Default: (2, "length")
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`
