```Julia
cosmological(U::UnitSystem) = 𝟑*darkenergydensity(U)*(hubble(U)/lightspeed(U))^2
```

Cosmological constant from Einstein's controversial theory expanded on by Hubble.

```Julia
julia> cosmological(Metric)
1.1056022912824226e-52

julia> cosmological(Hubble)
2.0667

julia> cosmological(Cosmological)
25.132741228718352
```
