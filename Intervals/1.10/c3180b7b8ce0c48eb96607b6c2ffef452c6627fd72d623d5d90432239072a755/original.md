```
HourBeginning{T<:TimeType, L, R} <: AbstractInterval{T}
```

A type alias for `AnchoredInterval{Hour(1), T}` which is used to denote a 1-hour period of time which begins at a time instant (of type `T`).

When constructing an instance of `HourBeginning{T}` the resulting interval will left-closed (of type `HourBeginning{T,Closed,Open}`).
