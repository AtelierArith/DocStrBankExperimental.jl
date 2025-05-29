```
struct TropicalSemiring{T<:Real} <: Semiring{T}
    val::T
end
```

Tropical semiring: $R = (ℝ, max, +, -∞, 0)$.
