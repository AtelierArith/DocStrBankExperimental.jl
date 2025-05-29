```
emitted_intensities(comp::Material, elm::Element, dose::AbstractFloat, e0::AbstractFloat, θtoa::AbstractFloat, Ω::AbstractFloat; mc=XPP, fc=ReedFluorescence)
emitted_intensities(comp::Material, dose::AbstractFloat, e0::AbstractFloat, θtoa::AbstractFloat, Ω::AbstractFloat; mc=XPP, fc=ReedFluorescence)
```

  * comp: The composition of the Material
  * elm: The ionized element
  * dose: Electron dose in nA⋅s
  * e0: Beam energy in eV
  * θtoa: Take off angle in radians
  * Ω: Solid angle steradians

  * returns Dict{CharXRay, <:AbstractFloat} containing characteristic X-rays and the emitted intensities.

Computes the intensity emitted from the sample at the take-off angle into the specified solid angle. The XPP and Reed fluorescence algorithms are used by default but any ϕ(ρz)-model in which the integral Fχ is normalized to the emission from a single shell may be used.
