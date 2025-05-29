```
compute_thermal_structure(Temp, X, Y, Z, Phase, s::LinearWeightedTemperature)
```

Weight average along distance

Do a weight average between two field along a specified direction

Given a distance (could be any array, from X,Y) -> the weight of F1 increase from the origin, while F2 decreases.

This function has been conceived for averaging the solution of McKenzie and half space cooling models, but it can be used to smooth the temperature field from continent ocean:

  * Select the boundary to apply;
  * transform the coordinate such that dist represent the perpendicular direction along which you want to apply this smoothening and in a such way that 0.0 is the point in which the weight of F1 is equal to 0.0;
  * Select the points that belongs to this area
  * compute the thermal fields {F1} {F2}
  * then modify F.
