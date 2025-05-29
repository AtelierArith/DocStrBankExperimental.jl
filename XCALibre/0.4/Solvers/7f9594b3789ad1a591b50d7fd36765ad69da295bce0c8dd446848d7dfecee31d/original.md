```
run!(
    model::Physics{T,F,M,Tu,E,D,BI}, config; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0
    ) where{T<:Transient,F<:Incompressible,M,Tu,E,D,BI} = 
begin
    residuals = piso!(model, config, pref=pref); #, pref=0.0)
    return residuals
end
```

Calls the incompressible transient solver using the PISO algorithm.

# Input

  * `model` represents the `Physics` model defined by user.
  * `config` Configuration structure defined by user with solvers, schemes, runtime and hardware structures configuration details.
  * `output` select the format used for simulation results from `VTK()` or `OpenFOAM()` (default = `VTK()`)
  * `pref` Reference pressure value for cases that do not have a pressure defining BC. Incompressible solvers only.

# Output

This function returns a `NamedTuple` for accessing the residuals (e.g. `residuals.Ux`) with the following entries:

  * `Ux`  - Vector of x-velocity residuals for each iteration.
  * `Uy`  - Vector of y-velocity residuals for each iteration.
  * `Uz`  - Vector of y-velocity residuals for each iteration.
  * `p`   - Vector of pressure residuals for each iteration.
