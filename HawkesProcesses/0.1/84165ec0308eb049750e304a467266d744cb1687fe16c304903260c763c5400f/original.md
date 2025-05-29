```
fit(events::Array{<:Number, 1}, maxT::Number, its::Int64)
```

# Arguments

  * `events` The array of event times to fit the Hawkes process too.
  * `maxT` The boundary time over which the events were observed.
  * `its` Number of iterations to sample for.

# Notes

  * All `events` must be unique
