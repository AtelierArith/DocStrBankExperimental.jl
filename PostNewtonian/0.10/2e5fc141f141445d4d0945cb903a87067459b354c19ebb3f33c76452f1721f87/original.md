```
orbital_evolution(pnsystem; kwargs...)
orbital_evolution(M₁, M₂, χ⃗₁, χ⃗₂, Ωᵢ; kwargs...)
```

Integrate the orbital dynamics of an inspiraling non-eccentric compact binary.

## Required arguments

The first argument to this function may be a single `PNSystem` that encodes these required arguments (as well as `Rᵢ`, `Λ₁`, and `Λ₂` among the keyword arguments), or the following may be given explicitly:

  * `M₁`: Initial mass of object 1
  * `M₂`: Initial mass of object 2
  * `χ⃗₁`: Initial dimensionless spin of object 1, `S⃗₁/M₁²`
  * `χ⃗₂`: Initial dimensionless spin of object 2, `S⃗₂/M₂²`
  * `Ωᵢ`: Initial orbital angular frequency

(Note that the explicit inputs require `Ωᵢ`, whereas `PNSystem`s require `vᵢ` as input.)

These parameters all describe the "initial" conditions.  See below for an explanation of the different meanings of "initial" and "first" in this context.  Note that the masses change in time as a result of tidal heating — though the changes are quite small throughout most of the inspiral.  The spins change direction due to precession, but also change in magnitude due to tidal heating.  Therefore, the values passed here are only precisely as given *precisely at* the moment of the initial data corresponding to the frequency `Ωᵢ`.

## Keyword arguments

Note that several of these keywords are given as Unicode but can also be given as the ASCII string noted.  For example, `Λ₁` may be input as `Lambda1` equivalently; the default values are the same, regardless.

  * `Λ₁=0` or `Lambda1`: Tidal-coupling parameter of object 1.
  * `Λ₂=0` or `Lambda2`: Tidal-coupling parameter of object 2.
  * `Ω₁=Ωᵢ` or `Omega_1`: First angular frequency in output data.  This may be less than `Ωᵢ`, in which case we integrate backwards to this point, and combine the backwards and forwards solutions into one seamless output.  (See next section.)
  * `Ωₑ=Ω(v=1,M=M₁+M₂)` or `Omega_e`: Final angular frequency at which to stop ODE integration.  Note that integration may stop before the system reaches this frequency, if we detect that PN has broken down irretrievably — for example, if one of the masses is no longer strictly positive, if a spin is super-extremal, or the PN velocity parameter `v` is decreasing, or is no longer in the range `(0,1)`.  Warnings will usually only be issued if `v < 0.35`, but if `quiet=true` informational messages will be issued.
  * `Rᵢ=Rotor(1)` or `R_i`: Initial orientation of binary.
  * `approximant="TaylorT1"`: Method of evaluating the right-hand side of the evolution equations.  Other possibilities are [`"TaylorT4"`](@ref TaylorT4!) and [`"TaylorT5"`](@ref TaylorT5!).  See the documentation of [`TaylorT1!`](@ref) for more details.
  * `PNOrder=typemax(Int)`: Order to which to retain powers of $v^2$ in PN expansions. The default is to include all available terms in each PN expression.
  * `check_up_down_instability=true`: Warn if the "up-down instability" (see below) is likely to affect this system.
  * `time_stepper=Vern9()`: Choice of solver in OrdinaryDiffEq to integrate ODE.
  * `abstol=eps(T)^(11//16)`: Absolute tolerance of ODE solver, where `T` is the common type to which all the positional arguments are promoted.  This is the tolerance on local error estimates, not necessarily the global error.  Note that `11//16` is just chosen to suggest that we will have roughly 11 digits of accuracy (locally) for `Float64` computations, and a similar accuracy for other float types *relative to* that type's epsilon.
  * `reltol=eps(T)^(11//16)`: Relative tolerance of ODE solver.  (As above.)
  * `termination_criteria_forwards=nothing`: Callbacks to use for forwards-in-time evolution.  See below for discussion of the default value.
  * `termination_criteria_backwards=nothing`: Callbacks to use for backwards-in-time evolution.  See below for discussion of the default value.
  * `force_dtmin=true`: If `dt` decreases below the integrator's own minimum, and this is false, the integrator will immediately raise an error, before the termination criteria have the chance to exit gracefully.  Note that a true value here is critical if the `dtmin_terminator` callback is to have any effect.
  * `quiet=true`: If set to `false`, informational messages about successful terminations of the ODE integrations (which occur when the target $v$ is reached in either direction) will be provided.  Warnings will still be issued when terminating for other reasons; if you wish to silence them too, you should do something like

    ```julia
    using Logging
    with_logger(SimpleLogger(Logging.Error)) do
        <your code goes here>
    end
    ```
  * `saves_per_orbit=0`: If greater than 0, the output will be interpolated so that there are `saves_per_orbit` time steps in the output for each orbit.  Note that this conflicts with the `saveat` option noted below.

All remaining keyword arguments are passed to the [`solve` function](https://github.com/SciML/DiffEqBase.jl/blob/8e6173029c630f6908252f3fc28a69c1f0eab456/src/solve.jl#L393) of `DiffEqBase`.  See that function's documentation for details, including useful keyword arguments.  The most likely important one is

  * `saveat`: Denotes specific times to save the solution at, during the solving phase — either a time step or a vector of specific times.

In particular, if you want the solution to be output at uniform time steps `δt`, you want to pass something like `saveat=δt`; you *don't want* the `solve` keyword `dt`, which is just the initial suggestion for adaptive systems.  It is not permitted to pass this option *and* the `saves_per_orbit` option.

Also note that `callback` can be used, and is combined with the callbacks generated by the `termination_criteria_*` arguments above.  That is, you can use the default ones *and* your own by passing arguments to `callback`.  See [the documentation](https://diffeq.sciml.ai/dev/features/callback_functions/) for more details, but note that if you want to make your own callbacks, you will need to add `OrdinaryDiffEq` to your project — or possibly even `DifferentialEquations` for some of the fancier built-in callbacks.

## ODE system

The evolved variables, in order, are

  * `M₁`: Mass of black hole 1
  * `M₂`: Mass of black hole 2
  * `χ⃗₁ˣ`: $x$ component of dimensionless spin of black hole 1
  * `χ⃗₁ʸ`: $y$ component...
  * `χ⃗₁ᶻ`: $z$ component...
  * `χ⃗₂ˣ`: $x$ component of dimensionless spin of black hole 2
  * `χ⃗₂ʸ`: $y$ component...
  * `χ⃗₂ᶻ`: $z$ component...
  * `Rʷ`: Scalar component of frame rotor
  * `Rˣ`: $x$ component...
  * `Rʸ`: $y$ component...
  * `Rᶻ`: $z$ component...
  * `v`: PN "velocity" parameter related to the total mass $M$ and orbital angular frequency $Ω$ by $v = (M Ω)^{1/3}$
  * `Φ`: Orbital phase given by integrating $Ω$

The masses and spin magnitudes evolve according to [`tidal_heating`](@ref).  The spin directions evolve according to [`Ω⃗ᵪ₁`](@ref) and [`Ω⃗ᵪ₂`](@ref).  The frame precesses with angular velocity [`Ω⃗ₚ`](@ref), while also rotating with angular frequency `Ω` about the [Newtonian orbital angular velocity direction](@ref ℓ̂).  The frame rotor $R$ is given by integrating the sum of these angular velocities as described in [Boyle (2016)](https://arxiv.org/abs/1604.08139).  And finally, the PN parameter $v$ evolves according to something like

$$
\dot{v} = - \frac{\mathcal{F} + \dot{M}_1 + \dot{M}_2} {\mathcal{E}'}
$$

where [`𝓕`](@ref) is the flux of gravitational-wave energy out of the system, $\dot{M}_1$ and $\dot{M}_2$ are due to tidal coupling as computed by [`tidal_heating`](@ref), and [`𝓔′`](@ref) is the derivative of the binding energy with respect to $v$.  For `"TaylorT1"`, the right-hand side of this equation is evaluated as given; for `"TaylorT4"`, the right-hand side is first expanded as a Taylor series in $v$ and then truncated at some desired order; for `"TaylorT5"`, the *inverse* of the right-hand side is expanded as a Taylor series in $v$, truncated at some desired order, and then inverted to obtain an expression in terms of $v$.

## Returned solution

The returned quantity is an [`ODESolution`](https://diffeq.sciml.ai/dev/basics/solution/) object, which has various features for extracting and interpolating the data.  We'll call this object `sol`.

!!! note
    The solution comes with data at the time points the ODE integrator happened to step to.  However, it *also* comes with dense output (unless you manually turn it off when calling `orbital_evolution`).  This means that you can interpolate the solution to any other set of time points you want simply by calling it as `sol(t)` for some vector of time points `t`.  The quantity returned by that will have all the features described below, much like the original solution.  Note that if you only want some of the data, you can provide the optional keyword argument `idxs` to specify which of the elements described below you want to interpolate.  For example, if you only want to interpolate the values of `M₁` and `M₂`, you can use `sol(t, idxs=[1,2])`.


The field `sol.t` is the set of time points at which the solution is given.  To access the `i`th variable at time step `j`, use `sol[i, j]`.[^1] You can also use colons.  For example, `sol[:, j]` is a vector of all the data at time step `j`, and `sol[i, :]` is a vector of the `i`th variable at all times.

[^1]: Here, the `i`th variable just refers to which number it has in the list of evolved   variables in the ODE system, as described under "ODE system".

For convenience, you can also access the individual variables with their symbols.  For example, `sol[:v]` returns a vector of the PN velocity parameter at each time step.  Note the colon in `:v`, which is [Julia's notation for a `Symbol`](https://docs.julialang.org/en/v1/base/base/#Core.Symbol).

## Initial frequency vs. first frequency vs. end frequency

Note the distinction between `Ωᵢ` (with subscript `i`) and `Ω₁` (with subscript `1`).  The first, `Ωᵢ`, represents the angular frequency of the *initial condition* from which the ODE integrator will begin; the second, `Ω₁`, represents the target angular frequency of the first element of the output data.  That is, the ODE integration will run forwards in time from `Ωᵢ` to the merger, and then — if `Ωᵢ>Ω₁` — come back to `Ωᵢ` and run backwards in time to `Ω₁`.  The output data will stitch these two together to be one continuous (forwards-in-time) data series.

For example, if you are trying to match to a numerical relativity (NR) simulation, you can read the masses and spins off of the NR data when the system is orbiting at angular frequency `Ωᵢ`.  Integrating the post-Newtonian (PN) solution forwards in time from this point will allow you to compare the PN and NR waveforms.  However, you may want to know what the waveform was at *earlier* times than are present in the NR data.  For this, you also have to integrate backwards in time.  We parameterize the point to which you integrate backwards with `Ω₁`.  In either case, element `1` of the output solution will have frequency `Ω₁` — though by default it is equal to `Ωᵢ`.

Similarly, the optional argument `Ωₑ=1` is the frequency of the `end` element of the solution — that is Julia's notation for the last element.  Note that this is automatically reduced if necessary so that the corresponding PN parameter $v$ is no greater than 1, which may be the case whenever the total mass is greater than 1.

## Up-down instability

Be aware that the [up-down instability](http://arxiv.org/abs/1506.09116) (where the more massive black hole has spin aligned with the orbital angular velocity, and the less massive has spin anti-aligned) can cause systems with nearly zero precession at the initial time to evolve into a highly precessing system either at earlier or later times.  This is a real physical result, rather than a numerical issue.  If you want to simulate a truly non-precessing system, you should explicitly set the in-place components of spin to precisely 0.  By default, we check for this condition, and will issue a warning if it is likely to be encountered for systems with low initial precession.  The function used to compute the unstable region is [`up_down_instability`](@ref).

## Time-stepper algorithms

`Tsit5()` is a good default choice for time stepper when using `Float64` with medium-low tolerance.  If stiffness seems to be impacting the results, `AutoTsit5(Rosenbrock23())` will automatically switch when stiffness occurs.  For tighter tolerances, especially when using `Double64`s, `Vern9()` or `AutoVern9(Rodas5P())` are good choices.  For very loose tolerances, as when using `Float32`s, it might be better to use `OwrenZen3()`.

## Termination criteria

The termination criteria are vital to efficiency of the integration and correctness of the solution.  The default values for forwards- and backwards-in-time evolution, respectively, are

```julia
CallbackSet(
    termination_forwards(v(Ω=Ωₑ, M=M₁+M₂)),
    dtmin_terminator(T),
    decreasing_v_terminator(),
    nonfinite_terminator()
)
```

and

```julia
CallbackSet(
    termination_backwards(v(Ω=Ω₁, M=M₁+M₂)),
    dtmin_terminator(T),
    nonfinite_terminator()
)
```

where `T` is the common float type of the input arguments.  If any additional termination criteria are needed, they could be added as additional elements of the `CallbackSet`s.  See the [callback documentation](https://diffeq.sciml.ai/stable/features/callback_functions/) for details.
