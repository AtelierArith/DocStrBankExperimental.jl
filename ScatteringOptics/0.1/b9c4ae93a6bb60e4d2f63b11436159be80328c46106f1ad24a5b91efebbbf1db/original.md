```julia
struct PeriodicBoxCarScatteringModel{T<:Number} <: ScatteringOptics.AbstractScatteringModel
```

An anistropic scattering model based on a thin-screen approximation. This scattering adopts the periodic boxcar field wonder described in Psaltis et al. 2018.

** Keywords for the constructor ** The default numbers are based on the best-fit parameters presented in Johnson et al. 2018.

  * `α::Number`: The power-law index of the phase fluctuations (Kolmogorov is 5/3).
  * `rin_cm::Number`: The inner scale of the scattering screen in cm.
  * `θmaj_mas::Number`: FWHM in mas of the major axis angular broadening at the specified reference wavelength.
  * `θmin_nas::Number`: FWHM in mas of the minor axis angular broadening at the specified reference wavelength.
  * `ϕ_deg::Number`: The position angle of the major axis of the scattering in degree.
  * `λ0_cm::Number`: The reference wavelength for the scattering model in cm.
  * `D_kpc::Number`: The distance from the observer to the scattering screen in pc.
  * `R_kpc::Number`: The distance from the source to the scattering screen in pc.
