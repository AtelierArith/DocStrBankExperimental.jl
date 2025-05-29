```julia
QuasiStatic(
    start_time::Number,
    end_time::Number,
    Δt::Number
) -> Cthonios.QuasiStatic{Vector{Int64}, T, U} where {T<:Number, U<:(Vector{T} where T<:Number)}

```

Method to construct a `QuasiStatic`. `start_time` - the initial time value. `end_time` - time to end the simulation. `Δt` - the time step to use for all time steps.
