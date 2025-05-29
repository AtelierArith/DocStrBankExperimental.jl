```
motion = Motion(action)
motion = Motion(action, time)
motion = Motion(action, time, spins)
```

Motion struct. It defines the motion, during a certain time interval, of a given group of spins. It is composed by three fields: `action`, which  defines the motion itself, `time`, which accounts for the time during which the motion takes place, and `spins`, which indicates the spins  that are affected by that motion.

# Arguments

  * `action`: (`::AbstractAction{T<:Real}`) action, such as [`Translate`](@ref) or [`Rotate`](@ref)
  * `time`: (`::TimeCurve{T<:Real}`, `=TimeRange(0.0)`) time information about the motion
  * `spins`: (`::AbstractSpinSpan`, `=AllSpins()`) spin indexes affected by the motion

# Returns

  * `motion`: (`::Motion`) Motion struct

# Examples

```julia-repl
julia> motion =  Motion(
            action = Translate(0.01, 0.0, 0.02),
            time = TimeRange(0.0, 1.0),
            spins = SpinRange(1:10)
       )
```
