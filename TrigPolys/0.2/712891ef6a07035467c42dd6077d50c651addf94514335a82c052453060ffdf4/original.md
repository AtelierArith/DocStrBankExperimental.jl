```
struct TrigPoly{T<:AbstractFloat, VT<:AbstractVector{T}}
    a0::T    # Constant coefficient
    ac::VT   # cos coefficients
    as::VT   # sin coefficients
end
```

Represents a *Hermitian trigonometric polynomial* by its coefficients. The vectors `ac` and `as` should have the same length, that we call `n` in this docstring. This represent the following function

```julia
R(ω) = a0 + sum(ac[k] * cos(k * ω) + as[k] * sin(k * ω) for k in 1:n)
```

which is a polynomial in the variable `x = cos(ω)`.
