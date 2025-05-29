```
prop_capillary(radius, flength, gas, pressure; λ0, λlims, trange, kwargs...)
```

Simulate pulse propagation in a hollow fibre using the capillary model.

# Mandatory arguments

  * `radius`: Core radius of the fibre. Can be a `Number` for constant radius, or a function   `a(z)` which returns the `z`-dependent radius.
  * `flength::Number`: Length of the fibre.
  * `gas::Symbol`: Filling gas species.
  * `pressure`: Gas pressure. Can be a `Number` for constant pressure, a 2-`Tuple` of `Number`s   for a simple pressure gradient, or a `Tuple` of `(Z, P)` where `Z` and `P`   contain `z` positions and the pressures at those positions.
  * `λ0`: (keyword argument) the reference wavelength for the simulation. For simple   single-pulse inputs, this is also the central wavelength of the input pulse.
  * `λlims::Tuple{<:Number, <:Number}`: The wavelength limits for the simulation grid.
  * `trange::Number`: The total width of the time grid. To make the number of samples a   power of 2, the actual grid used is usually bigger.

# Grid options

  * `envelope::Bool`: Whether to use envelope fields for the simulation. Defaults to `false`.   By default, envelope simulations ignore third-harmonic generation.   Plasma has not yet been implemented for envelope fields.
  * `δt::Number`: Time step on the fine grid used for the nonlinear interaction. By default,   this is determined by the wavelength grid. If `δt` is given **and smaller** than the   required value, it is used instead.

# Input pulse options

A single pulse in the lowest-order mode can be specified by the keyword arguments below. More complex inputs can be defined by a single `AbstractPulse` or a `Vector{AbstractPulse}`. In this case, all keyword arguments except for `λ0` are ignored.

  * `λ0`: Central wavelength
  * `τfwhm`: The pulse duration as defined by the full width at half maximum.
  * `τw`: The "natural" pulse duration. Only available if pulseshape is `sech`.
  * `ϕ`: Spectral phases to be applied to the transform-limited pulse. Elements are   the usual polynomial phases ϕ₀ (CEP), ϕ₁ (group delay), ϕ₂ (GDD), ϕ₃ (TOD), etc.
  * `energy`: Pulse energy.
  * `power`: Peak power **after any spectral phases are added**.
  * `pulseshape`: Shape of the transform-limited pulse. Can be `:gauss` for a Gaussian pulse   or `:sech` for a sech² pulse.
  * `polarisation`: Polarisation of the input pulse. Can be `:linear` (default), `:x`, `:y`,   `:circular`, or an ellipticity number -1 ≤ ε ≤ 1, where ε=-1 corresponds to left-hand circular,   ε=1 to right-hand circular, and ε=0 to linear polarisation. The major axis for   elliptical polarisation is always the y-axis.
  * `propagator`: A function `propagator!(Eω, grid)` which **mutates** its first argument to               apply an arbitrary propagation to the pulse before the simulation starts.
  * `shotnoise`:  If `true` (default), one-photon-per-mode quantum noise is included.

# Modes options

  * `modes`: Defines which modes are included in the propagation. Can be any of:

      * a single mode signifier (default: :HE11), which leads to mode-averaged propagation   (as long as all inputs are linearly polarised).
      * a list of mode signifiers, which leads to multi-mode propagation in those modes.
      * a `Number` `N` of modes, which simply creates the first `N` `HE` modes.

    Note that when elliptical or circular polarisation is included, each mode is present   twice in the output, once for `x` and once for `y` polarisation.
  * `model::Symbol`: Can be `:full`, which includes the full complex refractive index of the cladding   in the effective index of the mode, or `:reduced`, which uses the simpler model more   commonly seen in the literature. See `Luna.Capillary` for more details.   Defaults to `:full`.
  * `loss::Bool`: Whether to include propagation loss. Defaults to `true`.

# Nonlinear interaction options

  * `kerr`: Whether to include the Kerr effect. Defaults to `true`.
  * `raman`: Whether to include the Raman effect. Defaults to `false`.
  * `plasma`: Can be one of

      * `:ADK` – include plasma using the ADK ionisation rate.
      * `:PPT` – include plasma using the PPT ionisation rate.
      * `true` (default) – same as `:PPT`.
      * `false` – ignore plasma.

    Note that plasma is only available for full-field simulations.
  * `PPT_stark_shift::Bool`: when using the PPT ionisation rate, determines whether   to include the effect of the Stark shift of the ground-state energy levels.   *The necessary data is only available for helium, neon, and argon!*
  * `thg::Bool`: Whether to include third-harmonic generation. Defaults to `true` for   full-field simulations and to `false` for envelope simulations.

If `raman` is `true`, then the following options apply:     - `rotation::Bool = true`: whether to include the rotational Raman contribution     - `vibration::Bool = true`: whether to include the vibrational Raman contribution

# Output options

  * `saveN::Integer`: Number of points along z at which to save the field.
  * `filepath`: If `nothing` (default), create a `MemoryOutput` to store the simulation results   only in the working memory. If not `nothing`, should be a file path as a `String`,   and the results are saved in a file at this location. If `scan` is passed, `filepath`   determines the output **directory** for the scan instead.
  * `scan`: A `Scan` instance defining a parameter scan. If `scan` is given`, a`Output.ScanHDF5Output`is used to automatically name and populate output files of   the scan.`scanidx` must also be given.
  * `scanidx`: Current scan index within a scan being run. Only used when `scan` is passed.
  * `filename`: Can be used to to overwrite the scan name when running a parameter scan.   The running `scanidx` will be appended to this filename. Ignored if no `scan` is given.
  * `status_period::Number`: Interval (in seconds) between printed status updates.
