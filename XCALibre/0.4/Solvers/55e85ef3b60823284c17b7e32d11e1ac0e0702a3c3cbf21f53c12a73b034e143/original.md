```
run!(
    model::Physics{T,F,M,Tu,E,D,BI}; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0
    ) where{T<:Transient,F<:WeaklyCompressible,M,Tu,E,D,BI} = 
begin
    residuals = cpiso!(model, config)
    return residuals
end
```

Calls the compressible transient solver using the PISO algorithm for weakly compressible fluids.

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
  * `e`   - Vector of energy residuals for each iteration.
