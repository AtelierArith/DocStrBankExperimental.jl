```
BorisParticlePush(species, E, B, timestep)
```

This update step moves the particles of `species` subject to both an electric field, `E`, and a magnetic field, `B`. The method is frequently referred to by the shorthand accelerate-rotate-accelerate because the acceleration from the electric field is split in half, and applied before and after the magnetic field rotation.

An applied magnetic field forces charged particles to travel in circular orbits perpendicular to the magnetic field. Thus, a simulation using the Boris method only makes sense when there are at least two velocity components, and in this case, the applied magnetic field must be strictly perpendicular to the velocity components. So for example, one could have a 1d2v simulation with a spatial grid along the x-axis, and velocity components in the x and y directions. In this case, the magnetic field would be forced to point along the z axis. If all three velocity components are included in the simulation, then the magnetic field can point in any direction.

For more details on the method, see [Sections 4.3 and 4.4 of Birdsall and Langdon](@cite birdsall2004), or the [Boris' original conference proceedings](@cite boris1970).
