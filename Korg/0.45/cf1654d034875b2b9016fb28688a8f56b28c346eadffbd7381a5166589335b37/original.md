```
read_linelist(filename; format="vald", isotopic_abundances=Korg.isotopic_abundances)
```

Parse a linelist file, returning a vector of [`Line`](@ref)s.

The `format` keyword argument can be used to specify one of these linelist formats (default: `"vald"`):

  * `"vald"` for a [VALD](http://vald.astro.uu.se/%7Evald/php/vald.php) linelist. These can be either "short" or "long" format, "extract all" or "extract stellar".  Air wavelengths will automatically be converted into vacuum wavelengths, and energy levels will be automatically converted from cm$^{-1}$ to eV.
  * `"kurucz"` for an atomic or molecular [Kurucz linelist](http://kurucz.harvard.edu/linelists.html) (format=kurucz_vac if it uses vacuum wavelengths; be warned that Korg will not assume that wavelengths are vacuum below 2000 Å),
  * `"moog"` for a [MOOG linelist](http://www.as.utexas.edu/%7Echris/moog.html) (doesn't support broadening parameters or dissociation energies, assumed to be in vacuum wavelengths).
  * `"moog_air"` for a MOOG linelist in air wavelengths.
  * `"turbospectrum"` for a [Turbospectrum linelist](https://github.com/bertrandplez/Turbospectrum2019/blob/master/DOC/Readme-Linelist_format_v.19) in air wavelengths. Note that Korg doesn't make use of the (optional) orbital angular momentum quantum number, l, for the upper or lower levels, so it won't fall back on generic ABO recipes when the ABO parameters are not available. Korg's interpretation of the `fdamp` parameter is also slightly different from Turbospectrum's. See the documentation of the `vdW` parameter of [`Line`](@ref) for details.  Korg will error if encounters an Unsoeld fudge factor, which it does not support.
  * "turbospectrum_vac" for a Turbospectrum linelist in vacuum wavelengths.
  * "korg" for a Korg linelist (saved with hdf5). If the filename ends in `.h5`, this will be used by default.

For VALD and Turbospectrum linelists with isotope information available, Korg will scale log gf values by isotopic abundance (unless VALD has already pre-scaled them), using isotopic abundances from [NIST](https://www.nist.gov/pml/atomic-weights-and-isotopic-compositions-relative-atomic-masses) ([Korg.isotopic*abundances]). To use custom isotopic abundances, just pass `isotopic*abundances` with the same structure: a dict mapping atomic number to a dict mapping from atomic weight to abundance.

Be warned that for linelists which are pre-scaled for isotopic abundance, the estimation of radiative broadening from log(gf) is not accurate.

See also: [`load_ExoMol_linelist`](@ref), [`save_linelist`](@ref).
