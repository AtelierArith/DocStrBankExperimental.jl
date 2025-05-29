```
timecurve = TimeCurve(t, t_unit, periodic, periods)
```

TimeCurve struct. It is a specialized type that defines a time curve, which represents  the temporal behavior of motion. This curve is defined by two vectors:  `t` and `t_unit`, which represent the horizontal (x-axis) and vertical (y-axis) axes  of the curve, respectively. To some extent, this curve can be associated with animation curves, commonly found in software for video editing, 3D scene creation, or video game development.

Additionally, the TimeCurve struct contains two more fields, independent of each other: `periodic` is a Boolean that indicates whether the time curve should be repeated periodically. `periods` contains as many elements as repetitions are desired in the time curve.  Each element specifies the scaling factor for that repetition.

# Arguments

  * `t`: (`::AbstractVector{<:Real}`, `[s]`) time vector
  * `t_unit`: (`::AbstractVector{<:Real}`) y vector, it needs to be scaled between 0 and 1
  * `periodic`: (`::Bool`, `=false`) indicates whether the time curve should be periodically repeated
  * `periods`: (`::Union{<:Real,AbstractVector{<:Real}}`, `=1.0`): represents the relative duration    of each period with respect to the baseline duration defined by `t[end] - t[1]`.    In other words, it acts as a scaling factor to lengthen or shorten specific periods.    This allows for the creation of patterns such as arrhythmias or other variations in periodicity.

# Returns

  * `timecurve`: (`::TimeCurve`) TimeCurve struct

# Examples

1. Non-periodic motion with a single repetition: 

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 0.2, 0.5, 1.0])
```

![Time Curve 1](../assets/time-curve-1.svg)

2. Periodic motion with a single repetition:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 1.0, 1.0, 0.0], periodic=true)
```

![Time Curve 2](../assets/time-curve-2.svg)

3. Non-periodic motion with multiple repetitions:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 1.0, 1.0, 0.0], periods=[1.0, 0.5, 1.5])
```

![Time Curve 3](../assets/time-curve-3.svg)

4. Periodic motion with multiple repetitions:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 1.0, 1.0, 0.0], periods=[1.0, 0.5, 1.5], periodic=true)
```

![Time Curve 4](../assets/time-curve-4.svg)
