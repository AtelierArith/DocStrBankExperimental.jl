List of tools to analyze data from the AstroSat/UVIT payload processed with CCDLAB.

## UVIT Photometry

  * `read_ds9reg` : 	Read DS9 region file.
  * `uvit_aphot` : Perform aper photometry on UVIT images in any of the broadband filters.
  * `uvit_countrate2flux`: Convert count rate to flux density for any filter.
  * `uvit_filter2pha`: Generate source and PHA spectral files compatible with XSPEC from UVIT images in any of the filters.
  * `uvit_saturation_corr` : Perform saturation correction.
  * `uvit_zp_uc`: Print magnitude zero point and unit conversion factor using Tandon et al. 2020.

## Grating Spectroscopy

  * `xycen_from_ds9reg`: Read x,y centre for DS9 circular region file.
  * `write_uvit_grating_phafile`: Write PHA spectral file for UVIT gratings.
  * `fuv_grating1_count_spec`: Extract 1d count spectrum from FUV-Grating1 image file.
  * `fuv_grating1_net_countrate_spec`: Derive background-corrected net count rate spectrum from FUV-Grating1 image.
  * `fuv_grating1_pixel2lamA` : Convert FUV-Grating1 pixel numbers relative to zero order position into wavelength in Å.
  * `fuv_grating1_wavelength_calib`: Perform wavelength calibration of FUV-Grating1 count sectrum.
  * `fuv_grating1_flux_calib`: Perform flux calibration of FUV-Grating1 wavelength-calibrated count spectrum.
  * `fuv_grating1_fluxed_spec`: Generate wavelength and flux calibrated spectrum from FUV-Grating1 images.
  * `fuv_grating1_phafile`: Generate PHA spectral files from FUV-Grating1 images.
  * `fuv_grating1_ea` : Print FUV-Grating1 effective area.
  * `fuv_grating2_count_spec` : Extract 1d count spectrum from FUV-Grating2 image file.
  * `fuv_grating2_net_countrate_spec`: Derive background-corrected net count rate spectrum from FUV-Grating2 image.
  * `fuv_grating2_pixel2lamA`:  Convert FUV-Grating2 pixel numbers relative to zero order position into wavelength in Å.
  * `fuv_grating2_wavelength_calib`: Perform wavelength calibration of FUV-Grating2 count sectrum.
  * `fuv_grating2_flux_calib`: Perform flux calibration of FUV-Grating2 wavelength-calibrated count spectrum.
  * `fuv_grating2_fluxed_spec`: Generate wavelength and flux calibrated spectrum from FUV-Grating2 images.
  * `fuv_grating2_phafile`: Generate PHA spectral files from FUV-Grating2 images.
  * `fuv_grating2_ea`: Print FUV-Grating1 effective area.
  * `nuv_grating_m1_count_spec`: Extract 1d count spectrum from NUV-Grating image file.
  * `nuv_grating_m1_net_countrate_spec`: Derive background-corrected net count rate spectrum from NUV-Grating image.
  * `nuv_grating_m1_wavelength_calib`: Perform wavelength calibration of NUV-Grating count sectrum.
  * `nuv_grating_m1_flux_calib`: Perform flux calibration of NUV-Grating wavelength-calibrated count spectrum.
  * `nuv_grating_m1_fluxed_spec`: Generate wavelength and flux calibrated spectrum from NUV-Grating images.
  * `nuv_grating_phafile`: Generate PHA spectral files from NUV-Grating images.

## Unit conversions

  * `lambdaA2keV` : Convert wavelengh in Å to energy in keV.
  * `lambdaA2ergs` : Convert λ in Å to energy in ergs.
  * `flux_density_photons2cgs` : Convert photon flux density n*λ (photons/cm2/s/Å) to energy flux density f*λ (ergs/cm2/s/Å).
  * `flux_density_cgs2photons` : Convert flux density f*λ (ergs/cm2/s/Å) to photon number density n*λ (photons/cm2/s/Å).

To see detailed help for any tool (e.g., `nuv_grating_phafile`), type

```julia
julia>?
help?> nuv_grating_phafile
```
