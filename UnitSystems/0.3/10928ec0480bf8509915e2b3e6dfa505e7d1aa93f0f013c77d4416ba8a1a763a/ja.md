```Julia
cosmological(U::UnitSystem) = 𝟑*darkenergydensity(U)*(hubble(U)/lightspeed(U))^2
```

アインシュタインの物議を醸す理論からの宇宙定数は、ハッブルによって拡張されました。

```Julia
julia> cosmological(Metric)
1.1056022912824226e-52

julia> cosmological(Hubble)
2.0667

julia> cosmological(Cosmological)
25.132741228718352
```
