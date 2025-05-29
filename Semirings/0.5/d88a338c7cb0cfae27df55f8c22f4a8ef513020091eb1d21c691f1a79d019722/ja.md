```
struct LogSemiring{T<:Real} <: Semiring{T}
    val::T
end
```

対数半環: $R = (ℝ, ln(eˣ + eʸ), +, -∞, 0)$。
