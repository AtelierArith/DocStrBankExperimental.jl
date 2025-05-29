```
struct ProbSemiring{T<:Real} <: Semiring{T}
    val::T
end
```

Probability semiring: $R = (ℝ, +, ⋅, 0, +∞)$.
