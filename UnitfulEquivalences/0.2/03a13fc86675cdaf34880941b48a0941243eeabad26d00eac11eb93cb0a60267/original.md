```
Thermal()
```

Equivalence to convert between temperature and energy according to the relation $E = kT$, where

  * $E$ is the energy,
  * $T$ is the temperature and
  * $k$ is the Boltzmann constant.

# Example

```jldoctest
julia> uconvert(u"eV", 20u"°C", Thermal()) # room temperature is equivalent to ≈1/40 eV
0.025261712457978588 eV
```
