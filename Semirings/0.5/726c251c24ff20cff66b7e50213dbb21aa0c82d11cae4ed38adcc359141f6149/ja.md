```
struct ProbSemiring{T<:Real} <: Semiring{T}
    val::T
end
```

確率半環: $R = (ℝ, +, ⋅, 0, +∞)$。
