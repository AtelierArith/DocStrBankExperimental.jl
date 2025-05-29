```
settime(time::AbstractArray, step; start, stop, reftype, rotation)
```

Convert a column of time values to a [`ScaledArray`](@ref) for representing discretized time periods of uniform length. If `rotation` is specified (time values belong to multiple rotation groups), a [`RotatingTimeArray`](@ref) is returned with the `time` field being a [`ScaledArray`](@ref). The returned array ensures well-defined time intervals for operations involving relative time (such as [`lag`](@ref) and [`diff`](@ref)). See also [`aligntime`](@ref).

# Arguments

  * `time::AbstractArray`: the array containing time values.
  * `step=nothing`: the length of each time interval; try `step=one(eltype(time))` if not specified.

# Keywords

  * `start=nothing`: the first element of the `pool` of the returned [`ScaledArray`](@ref).
  * `stop=nothing`: the last element of the `pool` of the returned [`ScaledArray`](@ref).
  * `reftype::Type{<:Signed}=Int32`: the element type of the reference values for the [`ScaledArray`](@ref).
  * `rotation=nothing`: rotation groups in a rotating sampling design.
