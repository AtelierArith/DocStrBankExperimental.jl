```
apply_noise(smld::BasicSMLD, σ_psf::AbstractFloat)
```

Add localization uncertainty to 2D emitter positions based on photon counts.

# Arguments

  * `smld::BasicSMLD`: Input SMLD containing 2D emitters
  * `σ_psf::AbstractFloat`: PSF width in microns

# Returns

  * `BasicSMLD`: New SMLD with noisy positions and updated uncertainties

# Example

```julia
# Then add localization noise with specific PSF width
smld_noisy = apply_noise(smld_model, 0.13)  # 130nm PSF width
```
