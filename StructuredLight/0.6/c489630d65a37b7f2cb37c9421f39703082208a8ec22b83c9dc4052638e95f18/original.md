```
lens(x,y,fx,fy;k=1)
```

Output an array containing the phase shift introduced by a lens of focal lengths `fx` and `fy`.

The calculation is done over a grid defined by `x` and `y`.

`k` is the incident wavenumber.

To apply the lens at a beam `ψ₀`, just calculate `ψ = ψ₀ .* lens(x,y,fx,fy;k=k)`
