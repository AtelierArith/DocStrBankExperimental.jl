```
StateEquationIdealGas( ;sound_speed, reference_density, gamma, background_pressure=0.0,
                       clip_negative_pressure=false)
```

Equation of state to describe the relationship between pressure and density of a gas using the Ideal Gas Law.

# Keywords

  * `sound_speed`                 : Artificial speed of sound.
  * `reference_density`           : Reference density of the fluid.
  * `gamma`                       : Heat-capacity ratio
  * `background_pressure=0.0`     : Background pressure.
  * `clip_negative_pressure=false`: Negative pressure values are clipped to 0, which prevents spurious surface tension with `SummationDensity` but allows unphysical rarefaction of the fluid.
