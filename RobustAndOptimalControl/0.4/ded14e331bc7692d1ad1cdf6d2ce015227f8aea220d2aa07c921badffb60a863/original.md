```
diskmargin(L::LTISystem, σ::Real, ω)
```

Calculate the diskmargin at a particular frequency or vector of frequencies. If `ω` is a vector, you get a frequency-dependent diskmargin plot if you plot the returned value. See also [`ncfmargin`](@ref).
