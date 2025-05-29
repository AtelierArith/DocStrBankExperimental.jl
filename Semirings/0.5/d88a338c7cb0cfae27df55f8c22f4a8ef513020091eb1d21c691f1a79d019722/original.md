```
struct LogSemiring{T<:Real} <: Semiring{T}
    val::T
end
```

Logarithmic semiring: $R = (ℝ, ln(eˣ + eʸ), +, -∞, 0)$.
