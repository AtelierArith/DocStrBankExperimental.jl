```julia
struct Linear{T<:Real, U<:Real} <: MIPVerify.Layer
```

Represents matrix multiplication.

`p(x)` is shorthand for [`matmul(x, p)`](@ref) when `p` is an instance of `Linear`.

## Fields:

  * `matrix`
  * `bias`
