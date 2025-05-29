```
ParticleSwarmState{P,T} <: AbstractManoptSolverState
```

Describes a particle swarm optimizing algorithm, with

# Fields

  * `cognitive_weight`:          (`1.4`) a cognitive weight factor
  * `inertia`:                   (`0.65`) the inertia of the particles
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, eltype(swarm))`) an inverse retraction to use.
  * `retraction_method`:         (`default_retraction_method(M, eltype(swarm))`) the retraction to use
  * `social_weight`:             (`1.4`) a social weight factor
  * `stopping_criterion`:        (`[`StopAfterIteration`](@ref)`(500) | `[`StopWhenChangeLess`](@ref)`(1e-4)`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.
  * `vector_transport_method`:  (`default_vector_transport_method(M, eltype(swarm))`) a vector transport to use
  * `velocity`:                 a set of tangent vectors (of type `AbstractVector{T}`) representing the velocities of the particles

# Internal and temporary fields

  * `cognitive_vector`: temporary storage for a tangent vector related to `cognitive_weight`
  * `p`:                storage for the best point $p$ visited by all particles.
  * `positional_best`:  storing the best position $p_i$ every single swarm participant visited
  * `q`:                temporary storage for a point to avoid allocations during a step of the algorithm
  * `social_vec`:       temporary storage for a tangent vector related to `social_weight`
  * `swarm`:            a set of points (of type `AbstractVector{P}`) on a manifold $\{s_i\}_{i=1}^N$

# Constructor

```
ParticleSwarmState(M, initial_swarm, velocity; kawrgs...)
```

construct a particle swarm solver state for the manifold `M` starting at initial population `x0` with `velocities`, where the manifold is used within the defaults specified previously. All fields with defaults are keyword arguments here.

# See also

[`particle_swarm`](@ref)
