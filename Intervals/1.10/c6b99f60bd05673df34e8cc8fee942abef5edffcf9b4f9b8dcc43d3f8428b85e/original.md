```
HourEnding{T<:TimeType, L, R} <: AbstractInterval{T}
```

A type alias for `AnchoredInterval{Hour(-1), T}` which is used to denote a 1-hour period of time which ends at a time instant (of type `T`).

When constructing an instance of `HourEnding{T}` the resulting interval will right-closed (of type `HourEnding{T,Open,Closed}`).
