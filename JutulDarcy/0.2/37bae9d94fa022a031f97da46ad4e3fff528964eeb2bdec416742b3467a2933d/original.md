```
model, parameters = setup_reservoir_model(reservoir, system; wells = [], <keyword arguments>)
model, parameters = setup_reservoir_model(reservoir, system; wells = [w1, w2], backend = :csr, <keyword arguments>)
```

Set up a reservoir `MultiModel` for a given reservoir `DataDomain` typically set up from  [`reservoir_domain`](@ref) and an optional vector of wells that are created using [`setup_vertical_well`](@ref) and  [`setup_well`](@ref).

The routine automatically sets up a facility and couples the wells with the reservoir and that facility.

# Keyword arguments

## Basic model setup

  * `wells=[]`: Vector of wells (e.g. from [`setup_well`](@ref)) that are to be used in the model. Each well must have a unique name.
  * `extra_out=true`: Return both the model and the parameters instead of just the model.
  * `thermal = false`: Add additional equations for conservation of energy and temperature as a primary variable.
  * `kgrad=nothing`: Type of spatial discretization to use:

      * `:tpfa` or `nothing` gives standard two-point flux approximation (TPFA) with hard-coded two-point assembly
      * `:tpfa_test` gives TPFA with specialized finite-volume assembly. Should be similar in performance to `:tpfa`, but does not make use of threads.
      * `:avgmpfa` gives a consistent linear MPFA scheme that is more accurate for meshes with anisotropic perm or non-orthogonal cells than `:tpfa`.
      * `:ntpfa` gives a consistent nonlinear MPFA scheme (nonlinear version of `:avgmpfa` that preserves monotonicity)
  * `upwind=nothing`: Type of upwinding to use. Can be `:spu` or `nothing` for standard upwinding or `:weno` for a second-order weighted essentially non-oscillatory scheme.
  * `extra_outputs=Symbol[]`: Extra output variables for reservoir model. Defaults to "typical" values seen in reservoir simulation. Valid values: Vector of symbols to be output, `true` for all variables and `false` for the minimal set required to restart simulations (typically only the primary variables and mass of each component)

## Advanced model setup

Advanced options govern internals of the simulator, like type of automatic differentation, how equations are linearized and so on. These should not impact simulation results beyond what is allowed for the model tolerances, but can impact simulation speed.

  * `split_wells=false`: Add a facility model for each well instead of one facility model that controls all wells. This must be set to `true` if you want to use MPI or nonlinear domain decomposition.
  * `backend=:csr`: Backend to use. Can be `:csc` for serial compressed sparse column CSC matrix, `:csr` for parallel compressed sparse row matrix. `:csr` is a bit faster and is recommended when using MPI, HYPRE or multiple threads. `:csc` uses the default Julia format and is interoperable with other Julia libraries.
  * `context=DefaultContext()`: Context used for entire model. Not recommended to set up manually, use `backend` instead.
  * `assemble_wells_together=true`: Assemble wells in a single big matrix rather than many small matrices.
  * `block_backend=true`: Use block sparse representation. This is needed by the iterative solvers and corresponding preconditioners. Setting this to `false` will result in a direct solver being used. In addition, equations will be assembled in an order similar to that of MRST (equation major instead of cell major).
  * `general_ad=false`: Use more general form of AD. Will result in slower execution speed than if set to true, but can be useful when working with custom discretizations.
  * `discretization_arg=NamedTuple()`: Additional keyword arguments passed onto `discretized_domain_tpfv_flow` when setting up discretizations.

## Increment and variable options

These options govern the range of values and the maximum allowable change of properties over a single Newton iteration. Changing values for maximum change will not change the equations themselves, but the values will change the rate of nonlinear solver convergence. Typically, smaller values are more conservative and reduce numerical difficulties, but can significantly increase the number of iterations and the reduce the length of the average time-step. Setting very small values can make it infeasible to solve the problems in a reasonable time.

Note that relative values are usually given relative to the cell value. If your expected output values are close to zero (e.g. for near-atmospheric pressure) low values can lead to slow convergence.

  * `dp_max_abs=nothing`: Maximum allowable pressure change in SI units (Pa)
  * `dp_max_rel=0.2`: Maximum allowable relative pressure change (default is 20%)
  * `dp_max_abs_well=convert_to_si(50, :bar)`: Maximum allowable pressure change for wells in SI units (Pa)
  * `dp_max_rel_well=nothing`: Maximum allowable relative pressure change in well
  * `ds_max=0.2`: Maximum change in saturations
  * `dz_max=0.2`: Maximum change in composition (for compositional models only)
  * `p_min=JutulDarcy.DEFAULT_MINIMUM_PRESSURE`: Minimum pressure in model (hard limit)
  * `p_max=Inf`: Maximum pressure in model (hard limit)
  * `dr_max=Inf`: Maximum change in Rs/Rv for blackoil models over a Newton iteration. Taken relative to the saturated value of the cell.
  * `dT_max_rel=nothing`: Maximum relative change in temperature (JutulDarcy uses Kelvin, so comments about changing limits near zero above does not apply to typical reservoir temperatures)
  * `dT_max_abs=50.0`: Maximum absolute change in temperature (in °K/°C)
  * `T_min=convert_to_si(0.0, :Celsius)`: Minimum temperature in model (hard limit)
  * `fast_flash=false`: Shorthand to enable `flash_reuse_guess` and `flash_stability_bypass`. These options can together speed up the time spent in flash solver for compositional models. Options are based on "Increasing the Computational Speed of Flash Calculations With Applications for Compositional, Transient Simulations" by Rasmussen et al (2006).
  * `flash_reuse_guess=fast_flash`: Reuse previous flash guess when a cell remains in two-phase.
  * `flash_stability_bypass=fast_flash`: Bypass stability testing for cells outside the two-phase and shadow region.
  * `can_shut_wells=true`: Configure facility to allow shutting wells that repeatedly get rates with the wrong side. Disabling this can make certain models infeasible to simulate, but it can be useful to do so for simple models where you know that the wells should be operational.
