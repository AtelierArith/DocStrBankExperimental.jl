```
x, y, z = get_spin_coords(motionset, x, y, z, t)
```

Calculates the position of each spin at a set of arbitrary time instants, i.e. the time steps of the simulation.  For each dimension (x, y, z), the output matrix has $N_{	{spins}}$ rows and `length(t)` columns.

# Arguments

  * `motion`: (`::Union{NoMotion, MotionList{T<:Real}}`) phantom motion
  * `x`: (`::AbstractVector{T<:Real}`, `[m]`) spin x-position vector
  * `y`: (`::AbstractVector{T<:Real}`, `[m]`) spin y-position vector
  * `z`: (`::AbstractVector{T<:Real}`, `[m]`) spin z-position vector
  * `t`: horizontal array of time instants

# Returns

  * `x, y, z`: (`::Tuple{AbstractArray, AbstractArray, AbstractArray}`) spin positions over time
