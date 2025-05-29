```
AbstractTwoBodyRestSystem <: AbstractTwoBodyInPhaseSpaceLayout
```

An abstract type representing the phase space layout of a two-body system in which one particle is at rest in the system's frame.

Concrete subtypes of `AbstractTwoBodyRestSystem` typically specify the coordinate system used to parameterize the momentum of the non-resting particle, such as [`Energy`](@ref), [`SpatialMagnitude`](@ref), [`CenterOfMomentumEnergy`](@ref), or [`Rapidity`](@ref). The choice of coordinate system impacts how the momenta of the incoming particles are constructed.

This type serves as a base for defining custom layouts that rely on rest-frame assumptions for two-body scattering or decay processes, and it facilitates method dispatch in momentum construction functions like [`QEDbase._build_momenta`](@extref).

# See Also

  * [`TwoBodyRestSystem`](@ref): A concrete implementation of `AbstractTwoBodyRestSystem` that   supports various univariate coordinates for describing the non-resting particle.
