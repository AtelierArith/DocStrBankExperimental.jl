```
TwoBodyRestSystem{RESTIDX, COORD<:AbstractUnivariateCoordinate}
```

Represents a two-body scattering system in the rest frame of one of the particles, where one particle (identified by `RESTIDX`) is at rest and the other particle's momentum is described by a coordinate system `COORD`. The system uses various univariate coordinates, such as energy, rapidity, or center-of-momentum energy, to parameterize the momentum of the moving particle.

This type allows for easy construction of the incoming particle momenta using the phase space layout for two-body systems, commonly used in high-energy physics processes. The system supports different coordinate systems for defining the moving particle's momenta, including energy-based and rapidity-based layouts.

# Fields

  * `coord::COORD`: The coordinate type (`COORD`) used to describe the non-resting particle's momenta.

# Supported Coordinates

  * `Energy`: Defines the energy of the moving particle.
  * `SpatialMagnitude`: Defines the spatial momentum magnitude of the moving particle.
  * `CMSEnergy`: Defines the total center-of-mass energy of the system.
  * `Rapidity`: Defines the rapidity of the moving particle.

# Example Usages

The following examples show how to use different coordinate systems with `TwoBodyRestSystem` in conjunction with the `_build_momenta` interface.

### Example 1: Using `Energy` Coordinate

```Julia
psl = TwoBodyRestSystem(Energy(2))  # Particle 1 at rest, particle 2 described by its energy
in_coords = (100.0,)  # Energy of particle 2
momenta = build_momenta(proc, model, psl, in_coords)
```

This constructs the momenta assuming particle 1 is at rest, and particle 2 has an energy of 100 GeV.

### Example 2: Using `SpatialMagnitude` Coordinate

```Julia
psl = TwoBodyRestSystem(SpatialMagnitude(2))  # Particle 1 at rest, particle 2 described by its spatial magnitude
in_coords = (50.0,)  # Spatial momentum magnitude of particle 2
momenta = build_momenta(proc, model, psl, in_coords)
```

In this case, the moving particle's spatial momentum magnitude is given, and its energy is calculated based on its mass.

### Example 3: Using `CMSEnergy` Coordinate

```Julia
psl = TwoBodyRestSystem(1,CMSEnergy())  # Particle 1 at rest, particle 2 described by the center-of-mass energy
in_coords = (200.0,)  # Total center-of-mass energy of the system
momenta = build_momenta(proc, model, psl, in_coords)
```

Here, the center-of-mass energy of the system is provided, and the momenta of both particles are calculated while conserving energy and momentum.

### Example 4: Using `Rapidity` Coordinate

```Julia
psl = TwoBodyRestSystem(Rapidity(2))  # Particle 1 at rest, particle 2 described by its rapidity
in_coords = (1.0,)  # Rapidity of particle 2
momenta = _build_momenta(proc, model, psl, in_coords)
@assert isapprox(getMass(sum(momenta)),50.0)
```

In this case, the rapidity of particle 2 is given, and its energy and momentum are computed based on this parameter.

# Notes

  * `RESTIDX` is the index of the particle that is at rest in the system.
  * `COORD` specifies the coordinate type of the non-resting particle and must be a subtype of   `AbstractUnivariateCoordinate`.
  * The coordinate system should be compatible with the given particles and their masses,   otherwise, an error may occur during momentum construction.

# Throws

  * `ArgumentError` if invalid coordinates are used (e.g., unsupported coordinate types or   incompatible indices).
