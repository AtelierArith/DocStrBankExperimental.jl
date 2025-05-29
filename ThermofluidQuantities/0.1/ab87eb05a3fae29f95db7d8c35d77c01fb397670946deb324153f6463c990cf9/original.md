```
FrictionFactor(Re::ReynoldsNumber,ϵD::RoughnessRatio)
```

Return the Darcy friction factor for a pipe flow with the given Reynolds number and roughness ratio. The function chooses the laminar formula (f = 64/Re) if Reynolds number is smaller than 2100 and uses the Colebrook equation if Reynolds number is larger than 4000. For transitional Reynolds numbers it uses the laminar formula, but warns the user.   
