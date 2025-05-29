```
isphysical(raysplitter(s))
```

Return `true` if the given `raysplitters` have physically plausible properties.

Specifically, check if (φ is the incidence angle, θ the refraction angle):

  * Critical angle means total reflection: If θ(φ) ≥ π/2 then Tr(φ) = 0
  * Transmission probability is even function: Tr(φ) ≈ Tr(-φ) at ω = 0
  * Refraction angle is odd function: θ(φ) ≈ -θ(-φ) at ω = 0
  * Ray reversal is true: θ(θ(φ, pflag, ω), !pflag, ω) ≈ φ
  * Magnetic conservation is true: (ω*new(ω*new(ω, pflag), !pflag) ≈ ω
