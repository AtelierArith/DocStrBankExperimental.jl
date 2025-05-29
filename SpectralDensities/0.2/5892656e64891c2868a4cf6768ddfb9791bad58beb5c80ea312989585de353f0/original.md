```
struct GaussianCutoffSD{T <: AbstractSD} <: AbstractSD
```

GaussianCutoffSD represents a spectral density with a Gaussian frequency cutoff. It is parameterized by the underlying spectral density `J`, and the frequency cutoff `ωcutoff`. That is

$$
J_\mathrm{gauss}(\omega) = J(\omega)e^{-\omega^2/\omega_c^2}
$$

# Fields

  * `J::T`: The underlying spectral density.
  * `ωcutoff::Float64`: The frequency cutoff.
