Abstract base type for definitions of scattering processes. It is the root type for the process interface, which assumes that every subtype of `AbstractProcessDefinition` implements at least

```Julia
incoming_particles(proc_def::AbstractProcessDefinition)
outgoing_particles(proc_def::AbstractProcessDefinition)
```

which return a tuple of the incoming and outgoing particles, respectively.

An `AbstractProcessDefinition` is also expected to contain spin and polarization information of its particles. For this, the functions

```Julia
incoming_spin_pols(proc_def::AbstractProcessDefinition)
outgoing_spin_pols(proc_def::AbstractProcessDefinition)
```

can be overloaded. They must return a tuple of [`AbstractSpinOrPolarization`], where the order must match the order of the process' particles. A default implementation is provided which assumes [`AllSpin`](@ref) for every [`is_fermion`](@ref) particle and [`AllPolarization`](@ref) for every [`is_boson`](@ref) particle.

!!! note "Performance"
    It is very beneficial for the performance of derived functions if these functions return compile-time-known values.


On top of these spin and polarization functions, the following functions are automatically defined:

```Julia
multiplicity(proc_def::AbstractProcessDefinition)
incoming_multiplicity(proc_def::AbstractProcessDefinition)
outgoing_multiplicity(proc_def::AbstractProcessDefinition)
```

Which return the number of spin and polarization combinations that should be considered for the process. For more detail, refer to the functions' documentations.

Furthermore, to calculate scattering probabilities and differential cross sections, the following interface functions need to be implemented for every combination of `CustomProcess<:AbstractProcessDefinition`, `CustomModel<:AbstractModelDefinition`, and `CustomPhaseSpaceLayout<:AbstractPhaseSpaceLayout`.

```Julia
    _incident_flux(psp::InPhaseSpacePoint{CustomProcess,CustomModel})

    _matrix_element(psp::PhaseSpacePoint{CustomProcess,CustomModel})

    _averaging_norm(proc::CustomProcess)

    _is_in_phasespace(psp::PhaseSpacePoint{CustomProcess,CustomModel})

    _phase_space_factor(psp::PhaseSpacePoint{CustomProcess,CustomModel,CustomPhaseSpaceLayout})
```

Optional is the implementation of

```Julia

    _total_probability(psp::PhaseSpacePoint{CustomProcess,CustomModel,CustomPhaseSpaceLayout})

```

to enable the calculation of total probabilities and cross sections.
