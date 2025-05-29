```
NanosecondDateTime
```

Type representing an instance in time to nanosecond precision. It is made up of a standard `DateTime` plus a number of nanoseconds in addition to the millisecond resolution that `DateTime` offers.

# Accessor functions

  * [`datetime`](@ref): Return a `Dates.DateTime` giving the date and time of a `NanosecondDateTime` to millisecond precision.
  * [`nanoseconds`](@ref): Return a `Dates.Nanosecond` giving the additional number of nanoseconds beyond the millsecond precision of the `Date.DateTime` part.

# Other functions

  * [`nearest_datetime`](@ref): Return the `Dates.DateTime` nearest to the `NanosecondDateTime`.

# Extended `Dates` functions

  * `Date`: Return the `Date` part of a `NanosecondDateTime`.
  * `Time`: Return the `Time` part of a `NanosecondDateTime` to full ns precision.

!!! note
    `NanosecondDateTime`s can represent the whole range of `DateTime`s, but miniSEED files with nanosecond precision can only represent dates in the range 1677-09-21T00:12:43.145224192 to 2262-04-11T23:47:16.854775807. An `InexactError` will be thrown when attempting to convert `NanosecondDateTime`s outside of this range into `Int64`s.

