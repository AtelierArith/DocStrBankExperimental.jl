```
ParticleSwarmState{P,T} <: AbstractManoptSolverState
```

Describes a particle swarm optimizing algorithm, with

# Fields

  * `cognitive_weight`: a cognitive weight factor
  * `inertia`:          the inertia of the particles
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `social_weight`:    a social weight factor
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `velocity`:         a set of tangent vectors (of type `AbstractVector{T}`) representing the velocities of the particles

# Internal and temporary fields

  * `cognitive_vector`: temporary storage for a tangent vector related to `cognitive_weight`
  * `p::P`: a point on the manifold $\mathcal M$ storing the best point visited by all particles
  * `positional_best`:  storing the best position $p_i$ every single swarm participant visited
  * `q::P`: a point on the manifold $\mathcal M$ serving as temporary storage for interims results; avoids allocations
  * `social_vec`:       temporary storage for a tangent vector related to `social_weight`
  * `swarm`:            a set of points (of type `AbstractVector{P}`) on a manifold $\{a_i\}_{i=1}^{N}$

# Constructor

```
ParticleSwarmState(M, initial_swarm, velocity; kawrgs...)
```

construct a particle swarm solver state for the manifold `M` starting with the initial population `initial_swarm` with `velocities`. The `p` used in the following defaults is the type of one point from the swarm.

# Keyword arguments

  * `cognitive_weight=1.4`
  * `inertia=0.65`
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `social_weight=1.4`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-4)`: a functor indicating that the stopping criterion is fulfilled
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# See also

[`particle_swarm`](@ref)
