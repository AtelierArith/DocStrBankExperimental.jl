```
Chirp(b, ω₀)
```

Represents chirp according to

$$
H(\omega) =
\exp[-\im b(ω-ω_0)^2].
$$

# Example

```julia
julia> Chirp(austrip(5u"fs^2"), austrip(1.5u"eV"))
Chirp(b = 8545.5457 = 5.0000 fs², ω₀ = 0.0551 = 1.5000 eV)
```
