```
struct HardCutoffSD{T <: AbstractSD} <: AbstractSD
```

HardCutoffSD represents a spectral density with a hard frequency cutoff. It is parameterized by the underlying spectral density `J`, and the frequency cutoff `ωcutoff`. That is

$$
J_\mathrm{hard}(\omega) = J(\omega)\Theta(\omega_c - \omega)
$$

where $\Theta$ is the Heaviside theta function.

# Fields

  * `J::T`: The underlying spectral density.
  * `ωcutoff::Float64`: The frequency cutoff.
