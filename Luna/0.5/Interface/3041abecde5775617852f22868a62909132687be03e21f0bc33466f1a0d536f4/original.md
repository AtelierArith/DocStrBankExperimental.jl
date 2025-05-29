```
prop_gnlse(γ, flength, βs; λ0, λlims, trange, kwargs...)
```

Simulate pulse propagation using the GNLSE.

# Mandatory arguments

  * `γ::Number`: The nonlinear coefficient.
  * `flength::Number`: Length of the fibre.
  * `βs`: The Taylor expansion of the propagation constant about `λ0`.
  * `λ0`: (keyword argument) the reference wavelength for the simulation. For simple   single-pulse inputs, this is also the central wavelength of the input pulse.
  * `λlims::Tuple{<:Number, <:Number}`: The wavelength limits for the simulation grid.
  * `trange::Number`: The total width of the time grid. To make the number of samples a   power of 2, the actual grid used is usually bigger.

# Grid options

  * `δt::Number`: Time step on the fine grid used for the nonlinear interaction. By default,   this is determined by the wavelength grid. If `δt` is given **and smaller** than the   required value, it is used instead.

# Input pulse options

A single pulse can be specified by the keyword arguments below. More complex inputs can be defined by a single `AbstractPulse` or a `Vector{AbstractPulse}`. In this case, all keyword arguments except for `λ0` are ignored. Note that the current GNLSE model is single mode only.

  * `λ0`: Central wavelength
  * `τfwhm`: The pulse duration as defined by the full width at half maximum.
  * `τw`: The "natural" pulse duration. Only available if pulseshape is `sech`.
  * `ϕ`: Spectral phases to be applied to the transform-limited pulse. Elements are   the usual polynomial phases ϕ₀ (CEP), ϕ₁ (group delay), ϕ₂ (GDD), ϕ₃ (TOD), etc.
  * `energy`: Pulse energy.
  * `power`: Peak power **after any spectral phases are added**.
  * `pulseshape`: Shape of the transform-limited pulse. Can be `:gauss` for a Gaussian pulse   or `:sech` for a sech² pulse.
  * `polarisation`: Polarisation of the input pulse. Can be `:linear` (default), `:circular`,   or an ellipticity number -1 ≤ ε ≤ 1, where ε=-1 corresponds to left-hand circular,   ε=1 to right-hand circular, and ε=0 to linear polarisation. The major axis for   elliptical polarisation is always the y-axis.
  * `propagator`: A function `propagator!(Eω, grid)` which **mutates** its first argument to               apply an arbitrary propagation to the pulse before the simulation starts.
  * `shotnoise`:  If `true` (default), one-photon-per-mode quantum noise is included.

# GNLSE options

  * `shock::Bool`: Whether to include the shock derivative term. Default is `true`.
  * `raman::Bool`: Whether to include the Raman effect. Defaults to `true`.
  * `ramanmodel`; which Raman model to use, defaults to `:sdo` which uses a simple  damped oscillator model, defined `τ1` and `τ2` (which default to values commonly  used for silica). `ramanmodel` can also be set to `:SiO2` which uses the more  advanced model of Hollenbeck and Cantrell.
  * `loss`: the power loss [dB/m]. Defaults to 0.
  * `fr`: fractional Raman contribution to `γ`. Defaults to `fr = 0.18`.
  * `τ1`: the Raman oscillator period.
  * `τ2`: the Raman damping time.

# Output options

  * `saveN::Integer`: Number of points along z at which to save the field.
  * `filepath`: If `nothing` (default), create a `MemoryOutput` to store the simulation results   only in the working memory. If not `nothing`, should be a file path as a `String`,   and the results are saved in a file at this location. If `scan` is passed, `filepath`   determines the output **directory** for the scan instead.
  * `scan`: A `Scan` instance defining a parameter scan. If `scan` is given`, a`Output.ScanHDF5Output`is used to automatically name and populate output files of   the scan.`scanidx` must also be given.
  * `scanidx`: Current scan index within a scan being run. Only used when `scan` is passed.
  * `filename`: Can be used to to overwrite the scan name when running a parameter scan.   The running `scanidx` will be appended to this filename. Ignored if no `scan` is given.
  * `status_period::Number`: Interval (in seconds) between printed status updates.
