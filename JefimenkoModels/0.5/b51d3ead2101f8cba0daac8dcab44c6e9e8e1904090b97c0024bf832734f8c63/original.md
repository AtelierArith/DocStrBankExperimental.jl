```
t′(r̄::Coordinate, t:Time, r̄′::Coordinate, media::PropagationMedia)
```

Calculate the retarded-time at a source point `r̄′` for an observer at the space-time point (`r̄`,`t`) through a `propagation medium`.

# Arguments

  * `r̄::UnitfulCoordinateSystems.Coordinate`: spatial location of the observation point
  * `t::Unitful.Time`: time at the observation point
  * `r̄′::UnitfulCoordinateSystems.Coordinate`: spatial location of the source point
  * `media::PropagationMedia`: properties of the medium between r̄′ and r̄
