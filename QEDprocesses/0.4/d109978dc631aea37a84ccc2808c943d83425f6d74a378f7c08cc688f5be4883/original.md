```
ScatteringProcess <: AbstractProcessDefinition
```

Generic implementation for scattering processes of arbitrary particles. Currently, only calculations in combination with `PerturbativeQED` are supported. However, this is supposed to describe scattering processes with any number of incoming and outgoing particles, and any combination of spins or polarizations for the particles.

The [`isphysical`](@ref) function can be used to check whether the process is possible in perturbative QED.

!!! warning
    The computation of cross sections and probabilities is currently unimplemented.


## Constructors

```
ScatteringProcess(
    in_particles::Tuple{AbstractParticleType},
    out_particles::Tuple{AbstractParticleType},
    [in_sp::Tuple{AbstractSpinOrPolarization},
    out_sp::Tuple{AbstractSpinOrPolarization}]
)
```

Constructor for a ScatteringProcess with the given incoming and outgoing particles and their respective spins and pols. The constructor asserts that the particles are compatible with their respective spins and polarizations. If the assertion fails, an `InvalidInputError` is thrown.

The `in_sp` and `out_sp` parameters can be omitted in which case all spins and polarizations will be set to `AllSpin` and `AllPol` for every fermion and boson, respectively.
