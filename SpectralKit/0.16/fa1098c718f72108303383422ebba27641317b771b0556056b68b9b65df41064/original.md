```julia
struct BoundedLinear{T<:Real} <: SpectralKit.AbstractUnivariateTransformation
```

Transform the domain to `y ∈ (a, b)`, using $y = x ⋅ s + m$.

`m` and `s` are calculated and checked by the constructor; `a < b` is enforced.
