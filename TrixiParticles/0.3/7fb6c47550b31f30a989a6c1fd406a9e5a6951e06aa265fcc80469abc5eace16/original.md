```
StateEquationCole(; sound_speed, reference_density, exponent,
                  background_pressure=0.0, clip_negative_pressure=false)
```

Equation of state to describe the relationship between pressure and density of water up to high pressures.

# Keywords

  * `sound_speed`:             Artificial speed of sound.
  * `reference_density`:       Reference density of the fluid.
  * `exponent`:                A value of `7` is usually used for most simulations.
  * `background_pressure=0.0`: Background pressure.
  * `clip_negative_pressure=false`: Negative pressure values are clipped to 0, which prevents spurious surface tension with `SummationDensity` but allows unphysical rarefaction of the fluid.
