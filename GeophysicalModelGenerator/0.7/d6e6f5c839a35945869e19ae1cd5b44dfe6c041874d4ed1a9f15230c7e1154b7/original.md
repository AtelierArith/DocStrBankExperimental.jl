```
SpreadingRateTemp(Tsurface=0, Tmantle=1350, Adiabat=0, MORside="left",SpreadingVel=3, AgeRidge=0, maxAge=80)
```

Sets a halfspace temperature structure within the box, combined with a spreading rate (which implies that the plate age varies)

# Parameters

  * Tsurface : surface temperature [C]
  * Tmantle : mantle temperature [C]
  * Adiabat : Mantle Adiabat [K/km]
  * MORside : side of the box where the MOR is located ["left","right","front","back"]
  * SpreadingVel : spreading velocity [cm/yr]
  * AgeRidge : thermal age of the ridge [Myrs]
  * maxAge : maximum thermal Age of plate [Myrs]

Note: the thermal age at the mid oceanic ridge is set to 1 year to avoid division by zero
