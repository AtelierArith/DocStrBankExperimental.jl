```
λ_iterator(θ, s, m)
```

Construct an object to iterate over ₛλₗₘ values.

The $ₛλₗₘ(θ)$ function is defined as the spin-weighted spherical harmonic evaluated at spherical coordinates $(θ, ϕ)$, with $ϕ=0$.  In particular, note that it is real-valued. The return type is determined by the type of `θ` (or more precisely, cos½θ).

This algorithm by [Kostelec & Rockmore](@cite Kostelec_2008) allows us to iterate over increasing $ℓ$ values, for given fixed $s$ and $m$ values.

Note that this iteration has no inherent bound, so if you try to iterate over all values, you will end up in an infinite loop.  Instead, you can `zip` this iterator with another:

```julia
θ = 0.1
s = -2
m = 1
λ = λ_iterator(θ, s, m)
Δ = max(abs(s), abs(m))
for (ℓ, ₛλₗₘ) ∈ zip(Δ:Δ+5, λ)
    @show (ℓ, ₛλₗₘ)
end
```

Alternatively, you could use `Iterates.take(λ, 6)`, for example.

Note that the iteration always begins with `ℓ = Δ = max(abs(s), abs(m))`.
