```
PhaseSpacePoint
```

Representation of a point in the phase space of a process. Contains the process ([`AbstractProcessDefinition`](@extref QEDbase.AbstractProcessDefinition)), the model ([`AbstractModelDefinition`](@extref QEDbase.AbstractModelDefinition)), the phase space layout ([`AbstractPhaseSpaceLayout`](@extref QEDbase.AbstractPhaseSpaceLayout)), and stateful incoming and outgoing particles ([`AbstractParticleStateful`](@extref QEDbase.AbstractParticleStateful)).

The legality of the combination of the given process and the incoming and outgoing particles is checked on construction. If the numbers of particles mismatch, the types of particles mismatch (note that order is important), or incoming particles have an `Outgoing` direction, an error is thrown.

```julia
julia> using QEDcore

julia> using QEDbase.Mocks

julia> PhaseSpacePoint(
            MockProcess(),
            MockModel(),
            MockOutPhaseSpaceLayout(),
            (
                ParticleStateful(Incoming(), Electron(), SFourMomentum(1, 0, 0, 0)),
                ParticleStateful(Incoming(), Photon(), SFourMomentum(1, 0, 0, 0))
            ),
            (
                ParticleStateful(Outgoing(), Electron(), SFourMomentum(1, 0, 0, 0)),
                ParticleStateful(Outgoing(), Photon(), SFourMomentum(1, 0, 0, 0))
            )
        )
PhaseSpacePoint:
    process: one-photon Compton scattering
    model: perturbative QED
    phasespace layout: default
    incoming particles:
     -> incoming electron: [1.0, 0.0, 0.0, 0.0]
     -> incoming photon: [1.0, 0.0, 0.0, 0.0]
    outgoing particles:
     -> outgoing electron: [1.0, 0.0, 0.0, 0.0]
     -> outgoing photon: [1.0, 0.0, 0.0, 0.0]
```

!!! note
    `PhaseSpacePoint`s can be constructed with only one of their in- or out-channel set. For this, see the special constructors [`InPhaseSpacePoint`](@ref) and [`OutPhaseSpacePoint`](@ref). The [`InPhaseSpacePoint`](@ref) and [`OutPhaseSpacePoint`](@ref) type definitions can be used to dispatch on such `PhaseSpacePoint`s. Note that a full `PhaseSpacePoint` containing both its in- and out-channel matches both, .i.e. `psp isa InPhaseSpacePoint` and `psp isa OutPhaseSpacePoint` both evaluate to true if psp contains both channels. A completely empty `PhaseSpacePoint` is not allowed.

