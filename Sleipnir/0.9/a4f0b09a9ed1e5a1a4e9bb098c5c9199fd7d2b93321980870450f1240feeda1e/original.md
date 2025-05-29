```
partial_year(period::Type{<:Period}, float)
```

Calculate a partial year date based on a floating-point year value.

# Arguments

  * `period::Type{<:Period}`: The type of period to use (e.g., `Month`, `Day`).
  * `float::Float64`: The floating-point year value.

# Returns

  * `Date`: The calculated date corresponding to the partial year.
