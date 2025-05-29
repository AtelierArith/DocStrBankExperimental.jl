```
struct DebyeSD <: AbstractSD
```

DebyeSD represents a Debye spectral density. It is characterized by an amplitude `α` representing the strength of the coupling and the cutoff frequency `ωc`. That is

$$
J(\omega) = \frac{2\alpha}{\pi}\frac{\omega\omega_c^2}{\omega^2 + \omega_c^2}
$$

# Fields

  * `α::Float64`: The amplitude `α`, indicating the strength of the coupling.
  * `ωc::Float64`: The cutoff frequency.
