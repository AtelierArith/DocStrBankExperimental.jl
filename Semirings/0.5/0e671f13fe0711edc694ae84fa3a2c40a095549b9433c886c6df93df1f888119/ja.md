```
struct TropicalSemiring{T<:Real} <: Semiring{T}
    val::T
end
```

トロピカル半環: $R = (ℝ, \max, +, -∞, 0)$。
