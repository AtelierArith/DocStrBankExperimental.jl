```
effective_conductivity(f, σ₀, Rq, disttype=:normal)
```

Computes the effective conductivity in units of [S/m] due to surface roughness for a rough (or smooth) metallic surface that is many skin depths thick.  Uses a  fast rational function approximation of the Gradient model that is taken from D. N. Grujić,  "Simple and Accurate Approximation of Rough Conductor Surface Impedance," **IEEE Trans.  Microwave Theory Tech.**, vol. 70, no. 4, pp. 2053-2059, April 2022.

## Input Arguments

  * `f`:  The frequency [Hz].
  * `σ₀`: The DC bulk conductivity of the metal [S/m].
  * `Rq`: The RMS surface roughness [m].
  * `disttype`: The type of probability distribution used to model the roughness.  Choices are `:normal` (the default, used for the "oxide" side of printed conductors) and `:rayleigh` (used for the "foil" side of printed conductors).
