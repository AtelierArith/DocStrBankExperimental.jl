```
load_ExoMol_linelist(specs, states_file, transitions_file, upper_wavelength, lower_wavelength)
```

Load a linelist from ExoMol. Returns a vector of [`Line`](@ref)s, the same as [`read_linelist`](@ref).

# Arguments

  * `spec`: the species, i.e. the molecule that the linelist is for
  * `states_file`: the path to the ExoMol states file
  * `transitions_file`: the path to the ExoMol, transitions file
  * `upper_wavelength`: the upper limit of the wavelength range to load (Å)
  * `lower_wavelength`: the lower limit of the wavelength range to load (Å)

# Keyword Arguments

  * `line_strength_cutoff`: the cutoff for the line strength (default: -15) used to filter the linelist. See [`approximate_line_strength`](@ref) for more information.
  * `T_line_strength`: the temperature (K) at which to evaluate the line strength (default: 3500.0)

!!! warning
    This functionality is in beta.

