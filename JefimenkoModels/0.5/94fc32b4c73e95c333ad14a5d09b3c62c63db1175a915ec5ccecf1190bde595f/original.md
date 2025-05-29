```
t′(r̄::AbstractCoordinate, t:Time, r̄′::Coordinate, c::Quantity)
```

Calculate the retarded-time at a source point `r̄′` for an observer at the space-time point (`r̄`,`t`) through a medium with speed of light `c`.

# Arguments

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: spatial location of the observation point
  * `t::Unitful.Time`: time at the observation point
  * `r̄′::UnitfulCoordinateSystems.AbstractCoordinate`: spatial location of the source point
  * `c::Quantity`: Unitful speed of light in the medium between r̄′ and r̄
