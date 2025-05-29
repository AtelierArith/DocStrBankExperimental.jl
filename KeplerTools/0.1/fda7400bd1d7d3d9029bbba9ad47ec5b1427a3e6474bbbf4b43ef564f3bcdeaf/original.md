```
orb = fast_arrival_orbit(pkorb, v̄rel, tₛₚ)
```

Computes a arrival orbit from the parking orbit `pkorb`, the relative velocity at the patch `v̄rel`, the time at the patch `tₛₚ`. 

This function is faster than `arrival_orbit`, but may return sub-optimal trajectories for highly elliptical parking orbits. 
