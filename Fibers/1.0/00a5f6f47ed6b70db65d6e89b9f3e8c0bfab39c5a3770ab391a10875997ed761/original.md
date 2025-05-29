```
rumba_rec(dwi::MRI{T}, mask::MRI, odf_dirs::ODF=sphere_724, niter::Integer=600, λ_para::T=T(1.7*10^-3), λ_perp::T=T(0.2*10^-3), λ_csf::T=T(3.0*10^-3), λ_gm::T=T(0.8*10^-4), ncoils::Integer=1, coil_combine::String="SMF-SENSE", ipat_factor::Integer=1, use_tv::Bool=true) where T <: AbstractFloat
```

Perform robust and unbiased model-based spherical deconvolution (RUMBA-SD) reconstruction of DWIs, and return a `RUMBASD` structure.

If you use this method, please cite: Erick J. Canales-Rodríguez, et al. (2015). Spherical deconvolution of multichannel diffusion MRI data with non-Gaussian noise models and spatial regularization. PLoS ONE, 10(10), e0138910. https://doi.org/10.1371/journal.pone.0138910

# Arguments

  * `dwi::MRI{T}`: A series of DWIs, stored in an `MRI` structure with valid `.bvec` and `.bval` fields
  * `mask::MRI`: A brain mask volume, stored in an `MRI` structure
  * `odf_dirs::ODF=sphere_724`: The vertices and faces of the ODF tessellation, stored in an `ODF` structure
  * `λ_para::T=T(1.7*10^-3)`: Axial diffusivity in white-matter voxels with a single fiber population
  * `λ_perp::T=T(0.2*10^-3)`: Radial diffusivity in white-matter  voxels with a single fiber population
  * `λ_csf::T=T(3.0*10^-3)`: Mean diffusivity in CSF voxels
  * `λ_gm::T=T(0.8*10^-4)`: Mean diffusivity in gray-matter voxels
  * `ncoils::Integer=1`: Number of receive coil elements, if the DWIs were collected with parallel imaging, or 1 otherwise
  * `coil_combine::String="SMF-SENSE"`: Method that was used to combine signals from receive coil elements (possible values: "SMF-SENSE" or "SoS-GRAPPA"; has no effect if `ncoils` equals 1)
  * `ipat_factor::Integer=1`: Acceleration factor, if the DWIs were collected with parallel imaging, or 1 otherwise
  * `use_tv::Bool=true`: If true, include a total-variation regularization term in the FOD reconstruction

# Output

In the `RUMBASD` structure:

  * `.fodf`: Volume fractions of anisotropic compartments (one per vertex)
  * `.fgm`: Volume fraction of GM isotropic compartment
  * `.fcsf`: Volume fraction of CSF isotropic compartment
  * `.peak`: Orientation vectors of the 5 peak ODF amplitudes
  * `.gfa`: Generalized fractional anisotropy
  * `.var`: Estimated noise variance
  * `.snr_mean`: Estimated mean SNR
  * `.snr_std`: Estimated SNR standard deviation
