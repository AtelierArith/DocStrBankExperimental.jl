```
P(r̄::AbstractCoordinate, t::Time, model::JefimenkoModel; rtol=sqrt(eps))
```

Calculate the predicted Poynting vector 𝐏 observed at space-time point (`r̄`,`t`) using the electric and magnetic Jefimenko equations for a particular `model`. Calculate the integrals using a specified `relative tolerance`.

# Arguments

  * `r̄::UnitfulCoordinateSystems.AbstractCoordinate`: spatial location of the observation point
  * `t::Unitful.Time`: time at which the field is observed
  * `model::JefimenkoModel`: model of the transmitting source and propagation media

# Keywords

  * `rtol::Real`: relative tolerance at which to solve the integral (optional)
