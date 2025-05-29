```
struct ExponentialCutoffSD{T <: AbstractSD} <: AbstractSD
```

ExponentialCutoffSD represents a spectral density with an exponential frequency cutoff. It is parameterized by the underlying spectral density `J`, and the frequency cutoff `ωcutoff`. That is

$$
J_\mathrm{exp}(\omega) = J(\omega)e^{-\omega/\omega_c}
$$

# Fields

  * `J::T`: The underlying spectral density.
  * `ωcutoff::Float64`: The frequency cutoff.
