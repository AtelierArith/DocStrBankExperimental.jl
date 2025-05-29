```
BBH{T, PNOrder}
```

The [`PNSystem`](@ref) subtype describing a binary black hole system.

The `state` vector here holds the fundamental variables `M₁`, `M₂`, `χ⃗₁`, `χ⃗₂`, `R`, `v`, with the spins unpacked into three components each, and `R` unpacked into four — for a total of 13 elements.

Optionally, `Φ` may also be tracked as the 14th element of the `state` vector.  This is just the integral of the orbital angular frequency `Ω`, and holds little interest for general systems beyond a convenient description of how "far" the system has evolved.
