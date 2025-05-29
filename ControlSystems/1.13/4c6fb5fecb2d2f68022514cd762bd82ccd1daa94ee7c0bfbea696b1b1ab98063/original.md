```
lsim(sys::HammersteinWienerSystem, u, t::AbstractArray{<:Real}; x0=fill(0.0, nstates(sys)), alg=Tsit5(), abstol=1e-6, reltol=1e-6, kwargs...)
```

Simulate system `sys`, over time `t`, using input signal `u`, with initial state `x0`, using method `alg` .

# Arguments:

  * `t`: Has to be an `AbstractVector` with equidistant time samples (`t[i] - t[i-1]` constant)
  * `u`: Function to determine control signal `uₜ` at a time `t`, on any of the following forms:   Can be a constant `Number` or `Vector`, interpreted as `uₜ .= u` , or   Function `uₜ .= u(x, t)`, or   In-place function `u(uₜ, x, t)`. (Slightly more efficient)
  * `alg, abstol, reltol` and `kwargs...`: are sent to `OrdinaryDiffEq.solve`.

Returns an instance of [`SimResult`](@ref).
