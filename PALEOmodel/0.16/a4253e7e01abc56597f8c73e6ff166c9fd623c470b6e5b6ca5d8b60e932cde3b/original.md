```
SolverView(model, modeldata, arrays_idx; [verbose=true]) 
SolverView(model, modeldata, cellranges; [verbose=false], [indices_from_cellranges=true])
```

Provides a view on the whole or some part of the Model for a numerical solver.

Contains `PALEOboxes.VariableAggregator`s for a subset of spatial locations, defining state variables `S_all` composed of subsets `stateexplicit` (`S_e`), `statetotal` (`S_t`) and `state` (`S_a`).

Differential and algebraic constraints are provided by:

  * ODE paired `stateexplicit` (`S_e`) and `stateexplicit_deriv` (`dS_e/dt`), where `dS_e/dt = F(S_all)`.
  * Implicit-ODE paired `total` (`T`) and `total_deriv` (`dT/dt`), where `dT(S_all)/dt = F(S_all)`,    This implicitly determines the time derivative `dS_t/dt`, as `dT(S_all)/dt = dT(S_all)/dS_all * dS_all/dt`. The number of `total` (`T`) variables must equal the number of `statetotal` variables `S_t`.
  * Algebraic `constraint`s (`C`), where `C(S_all) = 0` and the number of `constraint` Variables `C` must  equal the number of `state` variables `S_a`.

If there are either no `total` (`T`) variables, or they are functions `T(S_e, S_t)` only of `S_e` and `S_t` (not of `S_a`), then  the state variables can be partitioned into subsets of differential variables `S_d` (consisting of `stateexplicit` (`S_e`) and `statetotal` (`S_t`)), and algebraic variables `state` (`S_a`).

The available choice of numerical solvers depends on the types of state variables in the model configuration:

  * A system with only `stateexplicit` (`S_e`) variables can be solved by an ODE solver (eg as a SciML `ODEProblem` by `PALEOmodel.ODE.integrate`).
  * Some ODE solvers (those that support a constant mass matrix on the LHS) can also solve systems with constraints `C` (eg as a SciML `ODEProblem` by `PALEOmodel.ODE.integrate`).
  * A DAE solver such as Sundials IDA is required to solve systems with implicit `total` (`T`) variables  (eg as a SciML `DAEProblem` by `PALEOmodel.ODE.integrateDAE`). NB: arbitrary combinations of `total` (`T`) and `constraint` (`C`) variables are *not* supported by Sundials IDA via `PALEOmodel.ODE.integrateDAE`, as the IDA solver option used to find consistent initial conditions requires a partioning  into differential and algebraic variables as described above.

Optional access methods provide an `ODE/DAE solver` view with composite `statevar` and `statevar_sms`,where:

```
- `statevar` is a concatenation of `stateexplicit`, `statetotal`, and `state` ([`set_statevar!`](@ref))
- `statevar_sms` is a concatenation of `stateexplicit_deriv`, `total_deriv`, `constraints` ([`get_statevar_sms!`](@ref))
```

Constructors create a [`SolverView`](@ref) for the entire model from `modeldata` array set `arrays_idx`,  or for a subset of Model Variables defined by the Domains and operatorIDs of `cellranges`. 

# Keywords

  * `indices_from_cellranges=true`: true to restrict to the index ranges from `cellranges`, false to just use `cellranges` to define Domains

and take the whole of each Domain.

  * `hostdep_all=true`: true to include host dependent not-state Variables from all Domains
  * `reallocate_hostdep_eltype=Float64`: a data type to reallocate `hostdep` Variables eg to replace any

AD types.
