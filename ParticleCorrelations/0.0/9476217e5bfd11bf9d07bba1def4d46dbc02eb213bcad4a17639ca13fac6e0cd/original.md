Specie

Represents a set of particles which are all the same. The type of particle is given by `Specie.particle` and the volume fraction this specie occupies is given by `Specie.volume_fraction`.

We can use `Specie.numberofparticles` to specify the number of particles, otherwise for an infinite `Specie.numberofparticles = Inf`.

The minimum distance between any two particles will equal `outer_radius(Specie) * Specie.separation_ratio`.
