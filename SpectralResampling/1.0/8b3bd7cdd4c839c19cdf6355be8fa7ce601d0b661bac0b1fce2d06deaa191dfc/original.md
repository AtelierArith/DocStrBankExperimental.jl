```
resample_conserving_flux(new_wave, old_wave, flux, err=nothing, mask=nothing; fill=NaN)
```

Resample flux (and optionally errors and a mask) onto a new wavelength grid, while convserving the flux.

# Required Arguments

  * `new_wave::AbstractVector`: The new 1D wavelength array that the flux should be resampled onto.
  * `old_wave::AbstractVector`: The original 1D wavelength array the the flux vector is currently sampled onto.
  * `flux::AbstractArray`: An n-dimensional flux array giving the fluxes at the specified wavelengths. The first axis of   this array should match the length of `old_wave`, while any additional axes will be treated as independent spectra.

# Optional Arguments

  * `err::AbstractArray`: An optional n-dimension error array giving the errors in the fluxes at   the specified wavelengths. The size of this array must match the size of `flux`.
  * `mask::BitArray`: An optional n-dimensional mask array containing boolean values   indicating whether certain flux values should be masked out. The size of this array must match the size of `flux`.   Note that the mask is NOT used in the calculation of the new fluxes – it is instead resampled in such a way that   the output mask will cover the same pixels that the input mask covered.

# Keyword Arguments

  * `fill::Real=NaN`: The fill value that is used to populate bins that are outside of the original wavelength range.
  * `verbose::Bool=true`: Whether or not to print a warning message if any bins fall outside of the original wavelength range.

# Returns

  * `new_fluxes::AbstractArray`: The fluxes that have been resampled onto the output wavelength grid. The first axis will   have the same length as `new_wave` whereas all other axes will be the same as the original `flux` array.

# Optional returns

  * `new_errs::AbstractArray`: Only returned if an input `err` is provided. These are the errors that have been resampled onto   the output wavelength grid. Will be the same size as `new_fluxes`.
  * `new_mask::BitArray`: Only returned if an input `mask` is provided. These are the new mask values that have been resampled   onto the output wavelength grid. Will be the same size as `new_fluxes`.

ADDITIONAL NOTES: 

```
- This module has been adapted from the SpectRes python package, https://github.com/ACCarnall/SpectRes,
  by Adam Carnall. Please refer to Carnall (2017): https://ui.adsabs.harvard.edu/abs/2017arXiv170505165C/abstract
  for an explanation of the theory behind the spectral resampling procedure. This function should perform
  identically to the `spectres.spectres` function from the original python version. However, there are some 
  minor differences enumerated below.

- This version uses a different convention by assuming the FIRST axis of the flux array is the wavelength axis 
  rather than the last axis in the python version (this was done for performance reasons, since julia is column-major 
  whereas python is row-major)

- There is an additional `mask` argument that allows one to input a mask as a BitArray the same size as `flux` and `err`.
  The mask will be combined by taking an `any` operation along all of the bins in the original flux array that are
  combined into the new bin in the output flux array. That is to say, if any of the points used from the orignal flux
  array to calculate the rebinned flux were masked out, then the new flux value will also be masked out.

- Care has been taken to improve the performance over the original python SpectRes package. This version is even faster than
  the numba-jitted version from the original package.
```
