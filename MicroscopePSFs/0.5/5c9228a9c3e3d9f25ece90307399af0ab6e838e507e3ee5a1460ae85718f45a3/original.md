```
calculate_fresnel_coefficients(kr2::Real, λ::Real, 
                             n_medium::Real, n_coverslip::Real, n_immersion::Real)
```

Calculate combined Fresnel transmission coefficients across all interfaces.

# Arguments

  * `kr2`: Squared lateral spatial frequency
  * `λ`: Wavelength in microns
  * `n_medium`: Refractive index of the sample medium
  * `n_coverslip`: Refractive index of the coverslip
  * `n_immersion`: Refractive index of the immersion medium

# Returns

  * Tuple of (Tp, Ts): Combined p and s polarization transmission coefficients
