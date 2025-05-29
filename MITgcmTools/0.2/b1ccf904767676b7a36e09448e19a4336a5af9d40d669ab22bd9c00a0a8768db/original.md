SeaWaterDensity(Θ,Σ,Π,Π0)

Compute potential density (ρP), in situ density (ρI), and density referenced to PREF (Π0 in decibars) from potential temperature (Θ in °C), salinity (Σ in psu) and pressure (Π in decibars) according to the UNESCO / Jackett & McDougall 1994 equation of state.

Credits: code based on a Matlab implementation by B. Ferron Reference: https://www.jodc.go.jp/info/ioc*doc/UNESCO*tech/059832eb.pdf Check value: ρI = `1041.83267kg/m^3` for Θ=`3°Celcius`, Σ=`35psu`, Π=`3000dbar`

```
(ρP,ρI,ρR) = SeaWaterDensity(3.,35.5,3000.)
isapprox(ρI,1041.83267, rtol=1e-6)
```
