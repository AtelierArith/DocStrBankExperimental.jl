```
History{M,T<:Real}
```

Linear event histories with marks of type `M` and temporal locations of type `T`.

# Fields

  * `times::Vector{T}`: sorted vector of event times
  * `marks::Vector{M}`: associated vector of event marks
  * `tmin::T`: start time
  * `tmax::T`: end time
