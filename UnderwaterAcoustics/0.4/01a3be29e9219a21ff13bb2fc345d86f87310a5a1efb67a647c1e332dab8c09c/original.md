```
soundspeed(temperature=27, salinity=35, depth=0; γ=0, cₐ=340, ρᵣ=1000)
```

Compute sound speed in water in m/s, given:

  * water `temperature` in °C
  * `salinity` in ppt
  * `depth` in meters
  * void fraction (`γ`) in bubbly water
  * sound speed in gas (`cₐ`) if `γ` > 0
  * ratio of density of water to gas (`ρᵣ`) if `γ` > 0

Implementation based on Mackenzie (1981), Wood (1964) and Buckingham (1997).
