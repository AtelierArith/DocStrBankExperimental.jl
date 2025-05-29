```
apply_noise(smld::BasicSMLD, σ_psf::Vector{<:AbstractFloat})
```

Add localization uncertainty to 3D emitter positions based on photon counts.

# Arguments

  * `smld::BasicSMLD`: Input SMLD containing 3D emitters
  * `σ_psf::Vector{<:AbstractFloat}`: PSF widths [σx, σy, σz] in microns

# Returns

  * `BasicSMLD`: New SMLD with noisy positions and updated uncertainties

# Example

```julia
# Then add localization noise with specific PSF widths
σ_psf = [0.13, 0.13, 0.39]  # 130nm lateral, 390nm axial
smld_noisy = apply_noise(smld_model, σ_psf)
```
