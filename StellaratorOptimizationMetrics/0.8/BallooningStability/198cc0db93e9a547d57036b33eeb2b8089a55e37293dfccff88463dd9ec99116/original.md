```
cobra_opt(eq, slist, nwells; θs, ζs, mode, geom_input, tokamak_input,
               lscreen, print_progress, interp, reltol, return_all, return_locs)
```

Calculates locations of maximally unstable eigenvalues

# Arguments

  * `eq::E`: A Vmec or DESC equilibrium
  * `slist::AbstractVector`: list of s values
  * `nwells::Integer`: Number of helical wells to include

# Optional inputs

  * `θs::AbstractVector`: Vector of starting θ values (in radians)
  * `ζs::AbstractVector`: Vector of starting ζ values (in radians normalized to field periods)
  * `reltol::Number`: Relative tolerance input for coefficient interpolation
  * `np::Integer`: Number of points used in eigenvalue calculation
  * `print_progress::Bool`: Print every time a new s-surface is used (adds excitement)
  * `spline::Bool`: interpolate using splines
  * 
