```
DelayLtiSystem{T, S}(sys::StateSpace, Tau::AbstractVector{S}=Float64[]) where {T <: Number, S <: Real}
```

Create a delayed system by specifying both the system and time-delay vector. NOTE: if you want to create a system with simple input or output delays, use the Function `delay(τ)`.
