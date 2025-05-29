```
struct LorentzianSD <: AbstractSD
```

LorentzianSD represents a Lorentzian spectral density. It is characterized by an amplitude `α` representing the strength of the coupling, the peak centre frequency `ω0`, and the width of the Lorentzian peak `Γ`.  That is

$$
J(\omega) = \frac{\alpha\Gamma}{\pi}\frac{\omega}{(\omega^2 - \omega_0^2)^2 + \omega^2\Gamma^2}
$$

# Fields

  * `α::Float64`: The amplitude `α`, indicating the strength of the coupling.
  * `ω0::Float64`: The centre frequency of the Lorentzian peak.
  * `Γ::Float64`: The width of the Lorentzian peak.
