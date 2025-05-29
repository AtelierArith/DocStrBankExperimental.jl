```
ParticleSampleable{V<:QEDlikeVariate}
```

Abstract base type for sampleable particle distributions and sampler in the context of `QEDevents.jl`. Here a particle-sampleable is generally a type which has some sort of `rand` function to produce random samples for properties of given particles, like four-momentum, spin, polarization, etc..

To implement the particle-sampleable interface, the following functions need to be given:

  * `Base.eltype(s::ParticleSampleable)`: return the innermost type of the samples
  * [`_weight(s::ParticleSampleable,x)`](@ref): return the weight of a given sample `x`
  * [`is_exact(s::ParticleSampleable)`](@ref): return wether or not a particle-sampleable is exact

Optionally, one can enhance the calculation of weights by providing

  * [`_assert_valid_input_type(s::ParticleSampleable,x)`](@ref): assert input has the correct type
  * [`_assert_valid_input(s::ParticleSampleable,x)`](@ref): assert input has correct properties
  * [`_post_processing(s::ParticleSampleable,x,res)`](@ref): apply some postprocesing to the result of `_weight`.

See [`weight`](@ref) for details. Furthermore, one can provide custom four-momentum types used for the generation of samples by implementing

  * [`_momentum_type(s::ParticleSampleable)`](@ref): return the momentum type used

For the actual sampling, one must implement

  * [`_randmom(d::ParticleSampleable)`](@ref): return momenta according to `d`

Using these interface functions, the following versions `rand` function are implemented. However, if in the particular case, there are more sophisticated implementations for the respective version of the `rand` function (see below), they can be implemented instead of `_randmom`. Nevertheless, in this case, it is recommended for convenience to implement a `_randmom` function as well, maybe using the result of `rand`.

!!! note "Single particle distribution"
    For `SingleParticleVariate`samplers, the single sample version `rand` is given:

    ```julia
    Distributions.rand(
        rng::Random.AbstractRNG,
        s::ParticleSampleable{SingleParticleVariate})
    ```

    which returns a random sample from `s` as a `ParticleStateful`.


!!! note "Multiple particle distribution"
    For `MultiParticleVariate` samplers, the mutating version of `rand` implemented:

    ```julia
    Distributions._rand!(
        rng::Random.AbstractRNG,
        s::ParticleSampleable{MultiParticleVariate},
        out::AbstractArray{ParticleStateful})
    ```

    which also provides implementations of `rand` for one or more samples.


!!! note "Scattering process distribution"
    For `ProcessLikeVariate` distributions, the single sample version of `rand` is given:

    ```julia
    Distributions.rand(
        rng::Random.AbstractRNG,
        s::ParticleSampleable{ProcessLikeVariate})
    ```

    which returns a `PhaseSpacePoint` including the respective scattering process, computation model and phase-space definition.

