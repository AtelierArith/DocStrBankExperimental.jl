```
get_modal_function(env, krs, freq, zr, zs)

Get the modal function for the Pekeris model.

# Arguments
- `env::PekerisUnderwaterEnv`: The underwater environment.
- `krs::Vector{Real}`: The horizontal wavenumbers.
- `freq::Real`: The frequency of the signal.
- `zr::Real`: The receiver depth.
- `zs::Real`: The source depth.

# Returns
- `Vector{Real}`: The modal function at the receiver depth.
- `Vector{Real}`: The modal function at the source depth.
```
