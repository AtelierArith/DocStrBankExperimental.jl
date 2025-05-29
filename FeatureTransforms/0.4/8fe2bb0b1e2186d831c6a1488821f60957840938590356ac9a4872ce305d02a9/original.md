```
Periodic{P, S}(f, period::P, [phase_shift::S]) <: Transform
```

Applies a periodic function `f` with provided `period` and `phase_shift` to the data.

The `period` and `phase_shift` must have the same supertype of `Real` or `Period`, depending on whether the data is `Real` or `TimeType` respectively.

!!! note
    For `TimeType` data, the result will change depending on the type of `period` given, even if the same amount of time is described. Example: `Week(1)` vs `Second(Week(1))`; the former starts the period on the most recent Monday, while the latter starts the period on the most recent multiple of 604800 seconds since time 0.


# Fields

  * `f::Union{typeof(cos), typeof(sin)}`: the periodic function
  * `period::Union{Real, Period}`: the function period. Must be strictly positive.
  * `phase_shift::Union{Real, Period}` (optional): adjusts the phase of the periodic function, measured in the same units as the input. Increasing the value translates the function to the right, toward higher/later input values.
