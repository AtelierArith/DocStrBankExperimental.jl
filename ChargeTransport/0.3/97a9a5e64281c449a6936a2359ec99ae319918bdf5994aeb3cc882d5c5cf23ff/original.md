```julia
mutable struct BulkRecombination
```

A struct holding all necessary information for building bulk recombination. With help of this constructor we can read out the indices the user chooses for electron and hole quasi Fermi potentials.

  * `iphin::Int64`: Index for FVM construction of electron quasi Fermi potential.

  * `iphip::Int64`: Index for FVM construction of hole quasi Fermi potential.

  * `bulk_recomb_Auger::Bool`: Boolean for present Auger recombination in bulk.

  * `bulk_recomb_radiative::Bool`: Boolean for present radiative recombination in bulk.

  * `bulk_recomb_SRH::Union{Type{ChargeTransport.SRHOff}, Type{ChargeTransport.SRHStationary}, Type{ChargeTransport.SRHTrapsStationary}, Type{ChargeTransport.SRHTrapsTransient}}`: DataType for present SRH recombination in bulk. This needs to be a Type due to cases with or without mobile traps.

  * `SRH_2species_trap::Union{Type{ChargeTransport.SRH2SpeciesPresentTrapDens}, Type{ChargeTransport.SRHOff}, Type{ChargeTransport.SRHStationary}}`: Data type with which you can include a stationary trap density to the right-hand side of the Poisson equation. This stationary trap density corresponds to the number of unoccupied trap states.
