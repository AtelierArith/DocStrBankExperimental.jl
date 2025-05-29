```
function run!(
    model::Physics, config; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0
    )

    # here an internal function is used for solver dispatch
    return residuals
end
```

This is the top level API function to initiate a simulation. It uses the user-provided `model` defined as a `Physics` object to dispatch to the appropriate solver.

# Dispatched flow solvers

  * Steady incompressible (SIMPLE algorithm for coupling)
  * Transient incompressible (PISO algorithm for coupling)
  * Steady weakly compressible (SIMPLE algorithm for coupling)
  * Transient weakly compressible (PISO algorithm for coupling)

# Input arguments

  * `model` reference to a `Physics` model defined by the user.
  * `config` Configuration structure defined by the user with solvers, schemes, runtime and hardware structures configuration details.
  * `output` select the format used for simulation results from `VTK()` or `OpenFOAM()` (default = `VTK()`)
  * `pref` Reference pressure value for cases that do not have a pressure defining BC. Incompressible solvers only (default = `nothing`)
  * `ncorrectors` number of non-orthogonality correction loops (default = `0`)
  * `inner_loops` number to inner loops used in transient solver based on PISO algorithm (default = `0`)

# Output

This function returns a `NamedTuple` for accessing the residuals (e.g. `residuals.Ux`). The fields available within the returned `residuals` tuple depend on the solver used. For example, for an incompressible solver, a x-momentum equation residual can be retrieved accessing the `Ux` field i.e. `residuals.Ux`. Look at reference guide for each dispatch method to find out which fields are available.

# Example

```julia
residuals = run!(model, config) 

# to access the pressure residual

residuals.p 
```
