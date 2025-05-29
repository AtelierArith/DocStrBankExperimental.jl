```julia
abstract type AbstractScatteringModel
```

An abstract anistropic scattering model based on a thin-screen approximation. In this package, we provide a reference implementation of the dipole (`DipoleScatteringModel`), von Mises (`vonMisesScatteringModel`) and periodic Box Car models (`PeriodicBoxCarScatteringModel`) all introduced in Psaltis et al. 2018.

**Mandatory fields** The scattering model will be fundamentally governed by the following parameters. Ideally, a subtype of this abstract model should have a constructor only with these arguments.

  * `α::Number`: The power-law index of the phase fluctuations (Kolmogorov is 5/3).
  * `rin::Number`: The inner scale of the scattering screen in cm.
  * `θmaj::Number`: FWHM in mas of the major axis angular broadening at the specified reference wavelength.
  * `θmin::Number`: FWHM in mas of the minor axis angular broadening at the specified reference wavelength.
  * `ϕ::Number`: The position angle of the major axis of the scattering in degree.
  * `λ0::Number`: The reference wavelength for the scattering model in cm.
  * `D::Number`: The distance from the observer to the scattering screen in cm.
  * `R::Number`: The distance from the source to the scattering screen in cm.

Furthermore the following parameters need to be precomputed.

  * `M::Number`: Magnification parameter, defined as D/R
  * `Qbar::Number`: The amplitudes of fluctuations. Given by `calc_Qbar(α, rin_cm, λ0_cm, M, θmaj_rad, θmin_rad)`
  * `C::Number`: The scaling factor of the power spectrum. Given by `calc_C(α, rin_cm, λ0_cm, Qbar)`
  * `D1maj::Number`: given by `calc_D1(α, Amaj, Bmaj)`
  * `D2maj::Number`: given by `calc_D2(α, Amaj, Bmaj)`
  * `D1min::Number`: given by `calc_D1(α, Amin, Bmin)`
  * `D2min::Number`: given by `calc_D2(α, Amin, Bmin)`

**Optional Fields** Followings are currently not used by methods but may be useful to have. 

  * `A::Number`: Asymmetry parameter θmaj*mas/θmin*mas
  * `ζ0::Number`: Another asymmetry parameter. Given by calc_ζ0(A)
  * `ϕ0`:: position angle (measured from Dec axis in CCW) converted to a more traditional angle in radians measured from RA axis in CW
  * `Amaj::Number`: related to the asymmetric scaling of the kernel. given by `calc_Amaj(rin_cm, λ0_cm, M, θmaj_rad)`
  * `Amin::Number`: related to the asymmetric scaling of the kernel. given by `calc_Amin(rin_cm, λ0_cm, M, θmin_rad)`
  * `Bmaj::Number`: calc*Bmaj(α, ϕ0, Pϕfunc, B*prefac)
  * `Bmin::Number`: calc*Bmin(α, ϕ0, Pϕfunc, B*prefac)

**Mandatory Method**

  * `Pϕ(sm::ScatteringModel, ϕ)`: Probability Distribution for the wondering of the direction of the magnetic field centered at orientation ϕ0.
