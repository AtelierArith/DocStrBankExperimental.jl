```
orb = fast_departure_orbit(pkorb, v̄rel, tₛₚ)
```

Computes a departure orbit from the parking orbit `pkorb`, the relative velocity at the patch `v̄rel`, the time at the patch `tₛₚ`. 

This function is faster than `departure_orbit`, but may return sub-optimal trajectories for highly elliptical parking orbits. 
