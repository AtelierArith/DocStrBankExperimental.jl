```
Spectral(; frequency=:linear, wavelength=:linear, wavenumber=:linear)
```

Equivalence that relates the energy of a photon to its (linear or angular) frequency, wavelength, and wavenumber. Whether to convert to linear or angular quantities is determined by optional keyword arguments, `:linear` is the default for all quantities.

Equivalent quantities are converted according to the relations $E = hf = ħω = hc/λ = ħc/ƛ = hcν̃ = ħck$, where

  * $E$ is the photon energy,
  * $f$ is the (temporal) frequency (`frequency=:linear`),
  * $ω$ is the angular frequency (`frequency=:angular`),
  * $λ$ is the wavelength (`wavelength=:linear`),
  * $ƛ$ is the angular (also called reduced) wavelength (`wavelength=:angular`),
  * $ν̃$ is the spectroscopic wavenumber (`wavenumber=:linear`),
  * $k$ is the angular wavenumber (`wavelength=:angular`),
  * $h$ is the Planck constant,
  * $ħ$ is the reduced Planck constant and
  * $c$ is the speed of light in vacuum.

# Examples

```jldoctest
julia> uconvert(u"nm", 13.6u"eV", Spectral()) # photon wavelength needed to ionize hydrogen
91.16485178911785 nm

julia> uconvert(u"Hz", 589u"nm", Spectral(frequency=:angular)) # angular frequency of sodium D line
3.1980501991661345e15 Hz
```
