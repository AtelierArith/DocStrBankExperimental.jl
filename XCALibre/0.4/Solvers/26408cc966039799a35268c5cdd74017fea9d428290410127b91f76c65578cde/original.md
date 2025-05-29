```
simple!(model_in, config; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0)
```

Incompressible variant of the SIMPLE algorithm to solving coupled momentum and mass conservation equations.

# Input arguments

  * `model` reference to a `Physics` model defined by the user.
  * `config` Configuration structure defined by the user with solvers, schemes, runtime and hardware structures configuration details.
  * `output` select the format used for simulation results from `VTK()` or `OpenFOAM` (default = `VTK()`)
  * `pref` Reference pressure value for cases that do not have a pressure defining BC. Incompressible solvers only (default = `nothing`)
  * `ncorrectors` number of non-orthogonality correction loops (default = `0`)
  * `inner_loops` number to inner loops used in transient solver based on PISO algorithm (default = `0`)

# Output

This function returns a `NamedTuple` for accessing the residuals (e.g. `residuals.Ux`) with the following entries:

  * `Ux` Vector of x-velocity residuals for each iteration.
  * `Uy` Vector of y-velocity residuals for each iteration.
  * `Uz` Vector of y-velocity residuals for each iteration.
  * `p` Vector of pressure residuals for each iteration.
