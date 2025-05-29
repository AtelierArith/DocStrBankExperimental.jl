```
EDF.TimestampedAnnotationList
```

A type representing a time-stamped annotations list (TAL).

Note that this type's constructor may attempt to round given `onset_in_seconds` and `duration_in_seconds` arguments to their nearest representable values in accordance with the EDF+ specification, which a) represents these values as ASCII, b) constrains these values to an 8 character limit, and c) does not allow the use of scientific notation for these fields.

See EDF+ specification for details.

# Fields

  * `onset_in_seconds::Float64`: onset w.r.t. recording start time (may be negative)
  * `duration_in_seconds::Union{Float64,Nothing}`: duration of this TAL
  * `annotations::Vector{String}`: the annotations associated with this TAL
