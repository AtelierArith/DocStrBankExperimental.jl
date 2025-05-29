```
pressure_f(env, krs, freq, r, zs, zr; t0 = 0.1, max_modes = Inf)

Compute the pressure field for the Pekeris model.

# Arguments
- `env::PekerisUnderwaterEnv`: The underwater environment.
- `krs::Vector{Real}`: The horizontal wavenumbers.
- `freq::Real`: The frequency of the signal.
- `r::Real`: The range.
- `zs::Real`: The source depth.
- `zr::Real`: The receiver depth.
- `t0::Real=0.1`: The time offset.
- `max_modes::Int=Inf`: The maximum number of modes to use.

# Returns
- `Complex{Real}`: The pressure field.
```
