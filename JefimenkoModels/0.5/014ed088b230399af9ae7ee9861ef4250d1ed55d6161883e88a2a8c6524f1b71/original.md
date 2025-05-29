```
H(r̄::AbstractCoordinate, t::Time, model::JefimenkoModel; rtol=sqrt(eps))
```

Calculate the predicted electric field 𝐇 observed at space-time point (`r̄`,`t`) using the electric Jefimenko equation for a particular `model`. Calculate the integral using a specified `relative tolerance`.

# Arguments

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: spatial location of the observation point
  * `t::Unitful.Time`: time at which the electric field is observed
  * `model::JefimenkoModel`: model of the transmitting source and propagation media

# Keywords

  * `rtol::Real`: relative tolerance at which to solve the integral (optional)
