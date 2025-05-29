```
α(tables::AbstractVector{String} [, profile=:hartmann_tran; kwargs...])
```

Computes the absorption coefficient using line-by-line data stored in the database tables specified in `tables`. The lineshape can be optionally specified using the `profile` argument and one of the Symbol keys `:hartmann_tran`, `:voigt`, `:sdvoigt`, `:lorentz`, `:gauss`. If no keyword arguments are specified, they will be automatically chosen from the tables provided.

# Keyword arguments

  * `components`: the components of the gas mixture for the calculation. Can be either a vector of tuples with `(molecule_id, local_iso_id)`               or a `Dict` with the `(molecule_id, local_iso_id)` tuple as key and the abundance as value. If the vector of tuples is supplied               the natural abundance will be used, so this makes no sense for gas mixtures other than isotopologues of the same molecule.
  * `intensity_threshold`: the minimum line strength in $cm^{-1}/(\text{molecule} \cdot cm^{-2})$
  * `pressure`: the environmental pressure in atmospheres (default: 1.0 atm)
  * `temperature`: the environmental temperature in Kelvin (default: 296.0 K)
  * `ν`: a vector or range of wavenumbers for which the absorption should be calculated. Useful for reusing the output ν vector for multiple calculations. If ν is supplied ν_range will be ignored.[]
  * `ν_range`: a tuple of the form (ν*min, ν*max) where ν*min/ν*max is the minimum/maximum wavenumber for the absorption_spectrum respectively in $cm^{-1}$
  * `ν_step`: the wavenumber step in $cm^{-1}$ (default: 0.01 $cm^{-1}$)
  * `ν_wing`: absolute calculation width of a line in $cm^{-1}$ (default: 0 $cm^{-1}$)
  * `ν_wing_hw`: relative calculation width of a line in multiples of a half-width (default: 50)
  * `diluent`: a `Dict` of the diluting substances, specified as `Symbol`, e.g. `:air` or `:H2O` for the key and the relative concentration as key (default: `Dict(:self => 1.0)`). See the example for details.
