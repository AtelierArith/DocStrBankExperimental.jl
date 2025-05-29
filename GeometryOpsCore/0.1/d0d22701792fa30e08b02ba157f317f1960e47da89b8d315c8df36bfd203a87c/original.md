```
abstract type Algorithm{M <: Manifold}
```

The abstract supertype for all GeometryOps algorithms.   These define how to perform a particular [`Operation`](@ref).

An algorithm may be associated with one or many [`Manifold`](@ref)s.   It may either have the manifold as a field, or have it as a static parameter  (e.g. `struct GEOS <: Algorithm{Planar}`).

## Interface

All `Algorithm`s must implement the following methods:

  * `rebuild(alg, manifold::Manifold)` Rebuild algorithm `alg` with a new manifold  as passed in the second argument.  This may error and throw a [`WrongManifoldException`](@ref) if the manifold is not compatible with that algorithm.
  * `manifold(alg::Algorithm)` Return the manifold associated with the algorithm.
  * `best_manifold(alg::Algorithm, input)`: Return the best manifold for that algorithm, in the absence of any other context.  WARNING: this may change in future and is not stable!

The actual implementation is left to the implementation of that particular [`Operation`](@ref).

## Notable subtypes

  * [`AutoAlgorithm`](@ref): Tells the [`Operation`](@ref) receiving  it to automatically select the best algorithm for its input data.
  * [`ManifoldIndependentAlgorithm`](@ref): An abstract supertype for an algorithm that works on any manifold. The manifold must be stored in the algorithm for a `ManifoldIndependentAlgorithm`, and accessed via `manifold(alg)`.
  * [`SingleManifoldAlgorithm`](@ref): An abstract supertype for an algorithm that only works on a  single manifold, specified in its type parameter.  `SingleManifoldAlgorithm{Planar}` is a special case that does not have to store its manifold, since that doesn't contain any information.  All other  `SingleManifoldAlgorithm`s must store their manifold, since they do contain information.
  * [`NoAlgorithm`](@ref): A type that indicates no algorithm is to be used, essentially the equivalent of `nothing`.
